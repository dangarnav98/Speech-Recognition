from tkinter import *
master = Tk()
master.geometry("280x280")
master.configure(background='powder blue')
master.title("Speech to text")
v1=StringVar()
import speech_recognition as sr  


def findout():
    r = sr.Recognizer()  
    with sr.Microphone() as source:                                                                       
        print("Speak:")                                                                                   
        audio = r.listen(source)   

    try:
        v1.set(r.recognize_google(audio))
    except sr.UnknownValueError:
        v1.set("Could not understand audio")
    except sr.RequestError as e:
        v1.set("Could not request results; {0}".format(e))
        
def findout2():
    v1.set(" ")
    r = sr.Recognizer()  
    with sr.Microphone() as source:                                                                       
        print("Speak:")                                                                                   
        audio = r.listen(source)   

    try:
        v1.set(r.recognize_google(audio))
    except sr.UnknownValueError:
        v1.set("Could not understand audio")
    except sr.RequestError as e:
        v1.set("Could not request results; {0}".format(e))

Label(master, text="Press the SPEAK button once and then speak",bg='black',fg='white').grid(row=1,padx=15)

b=Button(master,text="SPEAK",command=findout,bg='sky blue',bd=3,highlightthickness=4)
b.grid(row=3,column=0)

e1 = Entry(master,textvariable=v1)
e1.grid(row=4, column=0,padx=20,pady=10)


b1=Button(master,text="SPEAK again",command=findout2,bg='sky blue',bd=3,highlightthickness=4)
b1.grid(row=5,column=0)
b2=Button(master,text="Quit",command=master.destroy,bg='sky blue',bd=3,highlightthickness=4)
b2.grid(row=6,column=0)


master.mainloop( )