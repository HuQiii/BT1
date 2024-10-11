# BT1
import tkinter as tk
from tkinter import ttk
from tkinter import messagebox
from datetime import datetime


win = tk.Tk()
win.title("Bảng tính số tuổi")
win.geometry("400x300")  
win.configure(bg="#f0f0f0")  


frame1 = tk.LabelFrame(win, text="Thông tin ngày sinh", bg="#d1e7dd", fg="#0f5132", font=('Arial', 12, 'bold'))
frame1.grid(column=0, row=0, padx=10, pady=10, sticky=tk.W, ipadx=10)


ttk.Label(frame1, text="Ngày sinh (DD/MM/YYYY):", background="#d1e7dd", font=('Arial', 10)).grid(column=0, row=0, sticky=tk.W)
date_of_birth = tk.StringVar()
tk.Entry(frame1, textvariable=date_of_birth, font=('Arial', 10)).grid(column=0, row=1, pady=5)


frame2 = tk.LabelFrame(win, text="Chức năng", bg="#cfe2ff", fg="#1c1e21", font=('Arial', 12, 'bold'))
frame2.grid(column=0, row=1, padx=10, pady=10, sticky=tk.W)

def calculate_age():
    try:
       
        dob_str = date_of_birth.get()
        dob = datetime.strptime(dob_str, "%d/%m/%Y")
        
       
        today = datetime.today()
        age = today.year - dob.year - ((today.month, today.day) < (dob.month, dob.day))
        
        
        result.set(f"Tuổi: {age} năm")
    except ValueError:
        messagebox.showerror("Lỗi nhập liệu", "Vui lòng nhập ngày sinh đúng định dạng (DD/MM/YYYY)")


calculate_button = tk.Button(frame2, text="Tính tuổi", command=calculate_age, bg="#0d6efd", fg="white", font=('Arial', 10, 'bold'))
calculate_button.grid(column=0, row=0, pady=10)

frame3 = tk.LabelFrame(win, text="Kết quả", bg="#ffeeba", fg="#856404", font=('Arial', 12, 'bold'))
frame3.grid(column=0, row=2, padx=10, pady=10, sticky=tk.W)

result = tk.StringVar()
result_label = tk.Label(frame3, textvariable=result, bg="#ffeeba", font=('Arial', 10))
result_label.grid(column=0, row=0)

win.mainloop()
