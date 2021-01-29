# pytube
#This code will help you to download Youtube videos using python.
#created by Mohammad Rashid Nazir

import pytube
from tkinter import *

#starting functions
def download():
    video_url = url.get()
    try:
        youtube = pytube.YouTube(video_url)
        video = youtube.streams.get_highest_resolution()
        video.download('C://you tube//downloaded')
        notif.config(fg='green', text='Video Downloaded Successfully')
    except Exception as e:
        print(e)
        notif.config(fg='red', text='video could not be downloaded')

#front screen 
master = Tk()
master.title('Mohammad Rashid Nazir')

# Lables
Label(master, text='Youtube video Downloader', fg='red', font=('Algerian',16)).grid(sticky=N,padx=100,row=0)
Label(master, text='Please enter the link to your video blow: ', font=('Calibri',12)).grid(sticky=N,row=1, pady=15)
notif = Label(master, font=('Calibri',12))
notif.grid(sticky=N, pady=1, row=4)
#vriable
url = StringVar()
#Enrty here
Entry(master, width=50,textvariable=url).grid(sticky=N, row=2)
#download
Button(master, width=20, text='Download', font=('Times New Roman',12), command=download).grid(sticky=N, row=3, pady=15)

master.mainloop()


