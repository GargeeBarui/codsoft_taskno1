from tkinter import*
from tkinter import messagebox

def newTask():
    task = entry.get()
    if task != "":
        lb.insert(END,task)
        entry.delete(0,"end")
    else:
        messagebox.showwarning("warning")
def deleteTask():
    lb.delete(ANCHOR)
wb=Tk()
wb.geometry('400x350+400+150')
wb.title("today's work")  
wb.config(bg='#223441')


frame = Frame(wb)
frame.pack(pady=15)
lb = Listbox(
    frame,
    width=20,
    height=8,
    font=('times', 18),
    bd=0,
)
lb.pack(side=LEFT,fill=BOTH)

task_list = [
    "practice python",
    "study 6 hours",
    "eat meal",
    "learn new things",
    "do all task of today"
]

for item in task_list:
    lb.insert(END,item)

sb = Scrollbar(frame)
sb.pack(side=RIGHT,fill=BOTH)
lb.config(yscrollcommand=sb.set)
sb.config(command=lb.yview)

entry = Entry(
    wb,
    font=('times',10)
)

entry.pack(pady=15)

button_frame= Frame(wb)
button_frame.pack(pady=15)

addTask_button = Button(
    button_frame,
    text= "ADD",
    font=('times 10'),
    padx=10,
    pady=10,
    command=newTask
    )

addTask_button.pack(fill=BOTH, expand=True,side=LEFT)

delTask_button = Button(
    button_frame,
    text="DELETE",
    font=('times 10'),
    padx=10,
    pady=10,
    command=deleteTask
)
delTask_button.pack(fill = BOTH,expand=True, side=LEFT)

wb.mainloop()
