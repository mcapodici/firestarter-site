# Introduction

We are going to create a web application that let's people create their own AI chat bots. The chat bot would look something like this. This is a "Roasting Bot" that tries hard to insult you, but the app will let you create many types of bot.

![Chatbot idea sketch](../assets/chatbotideasketch-chatpiece.png)

To do this we will use

* Firestarter, of course
* OpenAI, to provide the intellegence for the bot

## Requirements

More specifically what we will build an app where:

* Someone, let's call them Lisa can come to this site and sign up.
* Lisa can create one or more chatbots.
* It will provide the code snippet for Lisa embed that chatbot on her sites.
* She embeds a chatbot on her blog, and then people can visit her blog and chat with that bot.

To avoid this costing you a lot of money, the users of this, such as Lisa need to bring their own OpenAI api key, and they pay for any credits they need to run the bot.

As such we have a very precious secret, so we need to secure it well. It deserves to be encrypted so that even the admin (you!) cannot see it by just browsing through the Firebase database.

## Visual Design and UX

This diagram shows what we are trying to build. It is definitely minimal and can be expanded upon later.

![Chatbot idea sketch](../assets/chatbotideasketch.png)

The top screen in the picture is the main admin page, where you can add bots, edit them, test them out. You can also enter you OpenAI API key here, which you must do to test and embed the bots.

When you add or edit a bot there are just 4 fields to set it up:

* Name: Whatever you want, just a reference for yourself, doesn't show up anywhere.
  
* Set Context: We send this text to ChatGPT first to get it "in the mood" to act like the bot you want to create, and some instruction to stay in character.

!!! info

    Be aware this is not fool proof and no matter how hard you try, someone will find a way to [break it out of chartacter](https://simonwillison.net/2022/Sep/16/prompt-injection-solutions/). 

* Use response to context as a message: If checked, the ChatGPT response to that context is shown to the user when they first interact with the bot.

* Initial message: If set, the first message the chat will be the bot, and it will use this message. If the checkbox above is ticked, this will be the first of the two messages shown.


## Next steps

[Bot Management >>>](chatbot-2.md){ .md-button }

