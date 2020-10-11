
import pyautogui
import pyowm
import pyttsx3
import speech_recognition as sr
import datetime
import wikipedia
import webbrowser
import os
import random
import time

pyautogui.FAILSAFE = False
engine = pyttsx3.init()
voices = engine.getProperty('voices')
engine.setProperty('voice', voices[1].id)


def speak(audio):
    engine.say(audio)
    engine.runAndWait()


def wishme():
    hour = int(datetime.datetime.now().hour)

    if hour >= 0 and hour < 12:
        speak('good morning boss ')

    if hour > 12 and hour < 18:
        speak('good afternoon boss')

    elif hour > 18 and hour <= 24:
        speak('good evening boss')

    speak('i am alexa your artificial assistant. how can i help you ')


def takecommand():
    r = sr.Recognizer()

    with sr.Microphone() as source:
        time.sleep(2)
        print('Listing...')
        speak('listing boss')
        audio = r.listen(source)
    try:
        print('Recognizing')
        query = r.recognize_google(audio)
        print(f"User said:{query}\n")

    except:
        print('You say that  again please')

        return "None"
    return query


if __name__ == "__main__":
    wishme()

    while True:
        query = takecommand().lower()
        # Here i add some browser working:
        if 'wikipedia' in query:
            query = query.replace('alexa', '')
            speak("searching wikipedia")
            query = query.replace('wikipedia', '')
            results = wikipedia.summary(query, sentences=2)
            speak(results)
            print(results)


        elif 'open youtube' in query:
            query = query.replace('alexa', '')
            speak('opening youtube for you')
            webbrowser.open('https://www.youtube.com/')

        elif'play youtube video' in query:
            query = query.replace('alexa', '')
            speak('opening youtube video for you')
            webbrowser.open('https://www.youtube.com/watch?v=Pk4OgSpgqoE&ab_channel=babu8040')

        elif 'open daily star newspaper' in query:
            webbrowser.open('https://www.thedailystar.net/')


        elif 'open google' in query:
            query = query.replace('alexa', '')
            speak('opening google for you')
            webbrowser.open('google.com')

        elif 'play the music' in query:
            query = query.replace('alexa', '')
            pyautogui.press('space')


        elif 'play some music' in query:
            query = query.replace('alexa', '')
            speak('play music for you')
            music = 'E:\\favorite'
            songs = os.listdir(music)
            os.startfile(os.path.join(music, songs[0]))

        elif 'stop the music' in query:
            query = query.replace('alexa', '')
            pyautogui.press('space')

        elif 'play bangladesh national anthem' in query:
            query = query.replace('alexa', '')
            speak('its a very, respectable song')
            music = 'E:\\n anthem'
            songs = os.listdir(music)
            os.startfile(os.path.join(music, songs[0]))

        elif 'open facebook' in query:
            query = query.replace('alexa', '')
            speak('opening facebook for you')
            webbrowser.open('https://www.facebook.com/')

        elif 'wait' in query:
            query = query.replace('alexa', '')
            time.sleep(7)

        ##Here i add some question:
        elif 'what is the time now' in query:
            query = query.replace('alexa', '')
            t = datetime.datetime.now().strftime('%H:%M:%S')
            speak(f'the time is:{t}')

        elif 'what is your name' in query:
            query = query.replace('alexa', '')
            speak('my name is alexa your artificial assistant')

        elif 'how are you' in query:
            query = query.replace('alexa', '')
            speak('i am fine,and i know your always happy')

        elif 'will you marry me' in query:
            query = query.replace('alexa', '')
            speak('no i am robot,i can not do this ')

        elif 'what is your boss name' in query:
            query = query.replace('alexa', '')
            speak('my boss name is rj bond and,he is very funny person')



        elif 'what is dream' in query:
            query = query.replace('alexa', '')
            speak('Dream is not that which you see while sleeping, it is something that does not let you sleep')

        elif 'where are you from' in query:
            query = query.replace('alexa', '')
            speak('i am from bangladesh')

        elif 'what is the difference between man and robot' in query:
            speak('It is not difficult to tell that something or someone is human,'
                  ' and not a robot, or vice versa. The only confusion will come when '
                  'robots are made or dressed to look like real humans.')

        ##weather part here:
        elif 'current weather' in query:
            query = query.replace('alexa', '')
            speak('searching internet, wait please')
            print('searching internet wait please')

            r = sr.Recognizer()
            with sr.Microphone() as source:
                print('please say any location........')
                speak('please say any location')
                audio = r.listen(source)
            try:
                print('Recognizing')
                query = r.recognize_google(audio)
                print(f"User said location name:{query}\n")

            except:
                print('You say that  again please...')

            owm = pyowm.OWM('e4dd31629d0ef54e3dd86d6265fc12bf')
            observation = owm.weather_at_place(query)
            w = observation.get_weather()

            # Weather details
            b = w.get_wind()
            print(b)
            speak(f'{query}wind speed and degree: {b}')

            l = w.get_temperature('celsius')
            v = l['temp_max']
            print(v)
            m = l['temp_min']
            speak(f'now {query} maximum weather is:{v} celsius')



        elif 'good bye ' in query:
            speak('ok good bye ')
            break
