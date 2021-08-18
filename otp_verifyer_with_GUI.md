- 👋 Hi, I’m @iBOYRAWANI
- 👀 I’m interested in so many things which i can't list
- 🌱 I’m currently pursuing mca

- 📫 How to reach me ...

<!---
iBOYRAWANI/iBOYRAWANI is a ✨ special ✨ repository because its `README.md` (this file) appears on your GitHub profile.
You can click the Preview link to take a look at your changes.
--->
# -*- coding: utf-8 -*-
"""
Created on Sat Jun  5 21:13:49 2021

@author: ANIKET SINGH RAWAT 
"""

from tkinter import *
from tkinter import messagebox
import smtplib
import random
root = Tk()
root.title("Send OTP Via Email")
root.geometry("500x350")
email_label = Label(root, text="Enter Email: ", font=("ariel 15 bold"), relief=FLAT)
email_label.grid(row=0, column=0, padx=7, pady=30)
email_entry = Entry(root, font=("ariel 15 bold"), width=25, relief=GROOVE, bd=2)
email_entry.grid(row=0, column=1, padx=6, pady=30)
email_entry.focus()
def send():
    try: 
        s = smtplib.SMTP("smtp.gmail.com" , 587)  # 587 is a port number 
        s.starttls()
        s.login("BPIBS.PROJECT.2020@GMAIL.COM", "Bpibs.project.2020")
        global otp
        otp = random.randint(100000, 999999)
        otp = str(otp)
        s.sendmail("BPIBS.PROJECT.2020@GMAIL.COM" , email_entry.get() , otp)
        messagebox.showinfo("Send OTP via Email", f"OTP sent to {email_entry.get()}")
        s.quit()
    
    except:
        messagebox.showinfo("Send OTP via Email", "Please enter the valid email address OR check an internet connection")
    
send_button = Button(root, text="Send Email", font=("ariel 15 bold"), bg="black", fg="green2", bd=3, command=send)
send_button.place(x=200, y=65)

otp_label = Label(root, text="Enter OTP : ", font=("ariel 15 bold"), relief=FLAT)
otp_label.grid(row=1, column=0, padx=7, pady=30)
global otp_entry
otp_entry = Entry(root, font=("ariel 15 bold"), width=25, relief=GROOVE, bd=2)
otp_entry.grid(row=1, column=1, padx=6, pady=30)
otp_entry.focus()

#code for verification of OTP from email
def otpv():
    
    a = otp_entry.get()
    if a == otp :
        messagebox.showinfo("OTP",("OTP Verified succesfully"))
    else:
        messagebox.showinfo("OTP",("please check otp or entered email"))

otp_button = Button(root, text="verify", font=("ariel 15 bold"), bg="black", fg="green2", bd=3, command=otpv)
otp_button.place(x=220, y=160)

root.mainloop()
