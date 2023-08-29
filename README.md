import tkinter as tk
from tkinter import *
from PIL import ImageTk,Image #PIL -> Pillow
import pymysql
from tkinter import messagebox
from AddBook import *
from DeleteBook import *
from ViewBooks import *
from IssueBook import *


mypass = "root" #use your own password
mydatabase="db" #The database name

con = pymysql.connect (host="localhost",user="root",password=mypass,database=mydatabase)
#root is the username here

cur = con.cursor() 

def open_login_page():
    selected_role = role_var.get()
    
    if selected_role == "Admin":
        open_admin_login_page()
    elif selected_role == "Vendor":
        open_vendor_login_page()
    elif selected_role == "User":
        open_user_login_page()

def open_admin_login_page():
         admin_login_window = tk.Toplevel(root)
         admin_login_window.title("Admin Login")
         admin_username_label = tk.Label(admin_login_window, text="admin Username:")
         admin_username_label.pack()

         admin_username_entry = tk.Entry(admin_login_window)
         admin_username_entry.pack()

         admin_password_label = tk.Label(admin_login_window, text="admin Password:")
         admin_password_label.pack()

         admin_password_entry = tk.Entry(admin_login_window, show="*")
         admin_password_entry.pack()

         admin_login_button = tk.Button(admin_login_window, text="Login", command=admin_login)
         admin_login_button.pack()

         admin_login_status_label = tk.Label(admin_login_window, text="")
         admin_login_status_label.pack()

         def admin_login():
             admin_username = admin_username_entry.get()
             admin_password = admin_password_entry.get()
             
             # Replace with actual admin login logic
             if admin_username == "admin" and admin_password == "password":
                 admin_login_status_label.config(text="Login successful!", fg="green")
             else:
                 admin_login_status_label.config(text="Login failed!", fg="red")
             

    
    

def open_vendor_login_page():
    vendor_login_window = tk.Toplevel(root)
    vendor_login_window.title("Vendor Login")
    vendor_username_label = tk.Label(vendor_login_window, text="Vendor Username:")
    vendor_username_label.pack()

    vendor_username_entry = tk.Entry(vendor_login_window)
    vendor_username_entry.pack()

    vendor_password_label = tk.Label(vendor_login_window, text="Vendor Password:")
    vendor_password_label.pack()

    vendor_password_entry = tk.Entry(vendor_login_window, show="*")
    vendor_password_entry.pack()

    vendor_login_button = tk.Button(vendor_login_window, text="Login", command=vendor_login)
    vendor_login_button.pack()

    vendor_login_status_label = tk.Label(vendor_login_window, text="")
    vendor_login_status_label.pack()

def vendor_login():
    vendor_username = vendor_username_entry.get()
    vendor_password = vendor_password_entry.get()
    
    # Replace with actual vendor login logic
    if vendor_username == "vendor" and vendor_password == "password":
        vendor_login_status_label.config(text="Login successful!", fg="green")
    else:
        vendor_login_status_label.config(text="Login failed!", fg="red")
    

def open_user_login_page():
    user_login_window = tk.Toplevel(root)
    user_login_window.title("User Login")
    user_username_label = tk.Label(user_login_window, text="user Username:")
    user_username_label.pack()

    user_username_entry = tk.Entry(user_login_window)
    user_username_entry.pack()

    user_password_label = tk.Label(user_login_window, text="user Password:")
    user_password_label.pack()

    user_password_entry = tk.Entry(user_login_window, show="*")
    user_password_entry.pack()

    user_login_button = tk.Button(user_login_window, text="Login", command=user_login)
    user_login_button.pack()

    user_login_status_label = tk.Label(user_login_window, text="")
    user_login_status_label.pack()

   

    






def user_login():
        user_username = user_username_entry.get()
        user_password = user_password_entry.get()
        
        # Replace with actual user login logic
        if user_username == "user" and user_password == "password":
            user_login_status_label.config(text="Login successful!", fg="green")
        else:
            user_login_status_label.config(text="Login failed!", fg="red")
        
   


root = tk.Tk()
root.title("Role Selection")


role_label = tk.Label(root, text="Select your role:")
role_label.pack()

roles = ["Admin", "Vendor", "User"]
role_var = tk.StringVar(value=roles[0])

role_option_menu = tk.OptionMenu(root, role_var, *roles)
role_option_menu.pack()

select_role_button = tk.Button(root, text="Confirm", command=open_login_page)
select_role_button.pack()


root.mainloop()
