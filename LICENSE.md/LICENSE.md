import requests
import random


# Method Request Twitt
def Twitt(Token,Counter):
    with requests.Session() as c:
        Num = 1
        activate = True
        while Num <= Counter and activate == True:
            x = random.randint(100000000, 10000000000)
            url = c.post('https://api.twitter.com/1.1/statuses/update.json',
                                headers={
                                    'authority':'api.twitter.com',
                                    'method':'POST',
                                    'accept':'*/*',
                                    'accept-encoding':'gzip, deflate, br',
                                    'authorization':'Bearer AAAAAAAAAAAAAAAAAAAAANRILgAAAAAAnNwIzUejRCOuH5E6I8xnZz4puTs%3D1Zv7ttfk8LF81IUq16cHjhLTvJu4FA33AGWWjCpTnA',
                                    'content-type':'application/x-www-form-urlencoded',
                                    'cookie':'ct0=198a0926052b1eb8f90049783ddd8354; auth_token='+Token,
                                    'user-agent':'Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/83.0.4103.61 Safari/537.36',
                                    'x-csrf-token':'198a0926052b1eb8f90049783ddd8354',
                                    },
                                data={'status':'#0xPHN '+str(x)})
            if url:
                print('True Twitt => ', x)
                Num = Num + 1
            else:
                print('Sorry, it was not Twitter!')
                activate = False



# Check Inputs
try:
    Token = str( input("Plase auth_token: ") )
    Counter = int( input("Plase Counter: ") )
    if Counter >= 201 or Counter <= 0:
        print("The entered number is greater than 200 or less than 0, so the value 50 will be set")
        Counter = 50
except:
    print("Auth_token must be text and Counter be a number")
else:
    Twitt(Token,Counter)
