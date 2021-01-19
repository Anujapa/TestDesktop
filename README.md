from tkinter import *
from time import sleep

# Code to add widget will go here……..
def remove_fl_char(param):
    return param[1:len(param)-1]

def get_data():
    data = ['"20201210102812"', '56.78', '87.88', '8', '78.67', '9', '45.66','7','67.88']
    print(data)
    data[0]=f'{data[0][:5]}:{data[0][5:7]}:{data[0][7:9]} {data[0][9:11]}-' \
        f'{data[0][11:13]}-{data[0][13:]}'
    return [f'TIMESTAMP : {remove_fl_char(data[0])}',
            f'RW OPEN CHANNEL FLOW : {data[1]} M^3/HR',
            f'RW TURBILITY : {data[2]} NTU',
            f'RW PH : {data[3]} PPM',
            f'PW TURBILITY : {data[4]} NTU',
            f'PW PH : {data[5]} PPM',
            f'PW CHLORINE : {data[6]} PPM',
            f'PW WATER SUMP LEVEL : {data[7]} METER',
            f'PW WATER FLOW : {data[8]} KG/CM^2']


window = Tk()

# creating the Box
window.title("DNP Systems,Pune")

# Determining the size of the Box
window.geometry('1000x800')
# Site : PURE WATER SYSTEMS, BARAV WTP
w = Label(window, text="DNP SYSTEMS, PUNE",width = "120",fg="white",bg="red",)
w.config(font=("Elephant", 44))
w.pack()
w = Label(window, text="SITE NAME : PURE WATER SYSTEM, BARAV WTP",width = "120",fg="white",bg="red",)
w.config(font=("Georgia", 20))
w.pack()
ws = Label(window, text="",width = "120",fg="black",bg='white')
ws.config(font=("Rockwell", 20))
ws.pack()

timestamp = Label(window, width="120", fg="black",bg='white')
timestamp.config(font=("Rockwell", 20))
timestamp.pack()
RW_OPEN_CHANNEL_FLOW = Label(window, width="120", fg="black",bg='white')
RW_OPEN_CHANNEL_FLOW.config(font=("Rockwell", 20))
RW_OPEN_CHANNEL_FLOW.pack()
RW_TURBILITY = Label(window, width="120", fg="black",bg='white')
RW_TURBILITY.config(font=("Rockwell", 20))
RW_TURBILITY.pack()
RW_PH=Label(window, width="120", fg="black",bg='white')
RW_PH.config(font=("Rockwell", 20))
RW_PH.pack()
PW_TURBILITY = Label(window, width="120", fg="black", bg='white')
PW_TURBILITY.config(font=("Rockwell", 20))
PW_TURBILITY.pack()
PW_PH = Label(window, width="120", fg="black", bg='white')
PW_PH.config(font=("Rockwell", 20))
PW_PH.pack()
PW_CHLORINE = Label(window, width="120", fg="black", bg='white')
PW_CHLORINE.config(font=("Rockwell", 20))
PW_CHLORINE.pack()
PW_WATER_SUMP_Level =Label(window, width="120", fg="black",bg='white')
PW_WATER_SUMP_Level.config(font=("Rockwell", 20))
PW_WATER_SUMP_Level.pack()
PW_WATER_Flow=Label(window, width="120", fg="black",bg='white')
PW_WATER_Flow.config(font=("Rockwell", 20))
PW_WATER_Flow.pack()
ws = Label(window, text="",width = "120",fg="black",bg='white')
ws.config(font=("Rockwell", 20))
ws.pack()

def update_text():
    data = get_data()
    timestamp.config(text=data[0])
    RW_OPEN_CHANNEL_FLOW.config(text=data[1])
    RW_TURBILITY.config(text=data[2])
    RW_PH.config(text=data[3])
    PW_TURBILITY.config(text=data[4])
    PW_PH.config(text=data[5])
    PW_CHLORINE.config(text=data[6])
    PW_WATER_SUMP_Level.config(text=data[7])
    PW_WATER_Flow.config(text=data[8])


update_text()

refresh = Button(window, bg='purple',fg="white", text="UPDATE",
                 command=update_text, compound=CENTER,font=("Garamond", 20))
refresh.pack()

window.configure(bg='white')
window.resizable(width=False, height=False)
window.mainloop()
