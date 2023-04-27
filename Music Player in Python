import tkinter
from tkinter import *
from tkinter import filedialog
from PIL import ImageTk, Image
from pygame import mixer
from tkinter.ttk  import Progressbar
mixer.init()
import os


# Create the main window
player = Tk()
player.geometry('500x300+200+150')
player.title('MUSIC PLAYER')
player.iconbitmap('music.ico')
player.configure()
images = Image.open('Purple_Floral.png')
bck_end = ImageTk.PhotoImage(images)
lbl = Label(player, image=bck_end)
lbl.place(x=0, y=0)
player.resizable(False, False)

# Initialize global variables

audiotrack = StringVar()
playlist = []

# Define functions
def volumeup():
    vol = mixer.music.get_volume()
    mixer.music.set_volume(vol + 0.1)

def volumedown():
    vol = mixer.music.get_volume()
    mixer.music.set_volume(vol - 0.1)

def nextmusic():
    # Get the index of the current playing song
    current_index = playlist.index(audiotrack.get())

    # Play the next song in the playlist
    if current_index < len(playlist) - 1:
        current_index += 1
    else:
        current_index = 0

    audiotrack.set(playlist[current_index])
    PlayingMusic()

def previousmusic():
    # Get the index of the current playing song
    current_index = playlist.index(audiotrack.get())

    # Play the previous song in the playlist
    if current_index > 0:
        current_index -= 1
    else:
        current_index = len(playlist) - 1

    audiotrack.set(playlist[current_index])
    PlayingMusic()

def PauseMusic():
    mixer.music.pause()

def PlayingMusic():
    music = audiotrack.get()
    mixer.music.load(music)
    mixer.music.play()

#def musicurl():
#   fname = filedialog.askopenfilename()
#  playlist.append(fname)
# audiotrack.set(fname)
#def musicurl():
#    fnames = filedialog.askopenfilenames()
#    for fname in fnames:
#        playlist.append(fname)
#        audiotrack.set(playlist[0])

#import os

def musicurl():
    directory = filedialog.askdirectory()
    if directory:
        for file in os.listdir(directory):
            if file.endswith('.mp3'):
                path = os.path.join(directory, file)
                playlist.append(path)
        if playlist:
            audiotrack.set(playlist[0])

def createwidthes():
    # Labels
    SearchLabel = Label(player, text='Load Songs', bg='white', font=('arial', 10, 'italic bold'))
    SearchLabel.grid(row=0, column=0, padx=10, pady=10)

    # Search Bar
    SearchBox = Entry(player, font=('arial', 10, 'italic bold'), width=40, textvariable=audiotrack)
    SearchBox.grid(row=0, column=1)

    # Buttons
    SearchButton = Button(player, text='Search', command=musicurl)
    SearchButton.grid(row=0, column=2, padx=10, pady=10)

    PlayButton = Button(player, text='Play', bg='red', width=10, command=PlayingMusic)
    PlayButton.grid(row=1, column=1, padx=10, pady=10)

    PauseButton = Button(player, text='Pause', bg='red', width=10, command=PauseMusic)
    PauseButton.grid(row=2, column=1, padx=10, pady=10)

    VolumeUpButton = Button(player, text='VolumeUp', bg='red', width=10, command=volumeup)
    VolumeUpButton.grid(row=1, column=0, padx=10, pady=10)

    VolumeLowButton = Button(player, text='VolumeLow', bg='red', width=10, command=volumedown)
    VolumeLowButton.grid(row=1, column=2, padx=10, pady=10)

    NextButton = Button(player, text='Next', bg='red', width=10,command=nextmusic)
    NextButton.grid(row=2, column=0, padx=10, pady=10)

    PreviousButton = Button(player, text='Previous', bg='red', width=10,command=previousmusic)
    PreviousButton.grid(row=2, column=2, padx=10, pady=10)

createwidthes()
# Run the GUI
player.mainloop()
