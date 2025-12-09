---
layout: "post"
title: "Say Hello, world! with Gemini"
author: Hae Seong Lee
categories: 
 - Programming
tags:
 - Gemini
date: 2025-12-09
---

*A spectre is haunting the World; the spectre of Artificial Intelligence.*

In my first post, I would like to share my experience of making an AI-powered Python script. Following the old tradition in all programming classes, I have started with the “Hello, world!” program. This is a silly little program that prints “Hello, world!” when executed and then terminates. However, we will do that with Gemini, like a Rube Goldberg machine.

Goodbye, old world!
==========

A typical “Hello, world!” program looks like this.

```python
def main():
    print("Goodbye, old world!")

if(__name__=="__main__"):
    main()
```

We have the main function whose only job is to print “Hello, world!”. Then we added the if statement that calls the main function when the script is executed as the main program. How can we transform this script into the AI era?

Set up Gemini in Python
========

In order to revolutionize our “Hello, world!” program, we need a Gemini API key and an appropriate Python library that provides us with Gemini features.

Get the Gemini API key
-------

We can get the Gemini API key pretty easily. Access the [Google AI Studio](https://aistudio.google.com) with this link. You will probably be taken to the welcome page. Be calm, and click the “Get started” button. After logging in, you will find the Get the API key at the bottom left of the page. Then you can make an API key there.

Install and set up the google-genai library
--------

The google-genai is a Python library that enables us to use Gemini features in Python. Assuming that you have Python installed in your environment, a simple pip (or pip3) will work.

```bash
pip3 install google-genai
```

Hello, new world!
=======

Now let’s write the “Hello, world!” program that is powered by Gemini. Our program looks a little bit more complicated than the previous one.

```python
from google import genai

def main():
    client=genai.Client(api_key="#put your Gemini API key here.")
    response=client.models.generate_content(model="gemini-2.5-flash",contents="Say Hello, world!")
    print(response.text)

if(__name__=="__main__"):
    main()
```

In the first line of the script, we import the google-genai library, which enables us to access Gemini in Python. Then we make a Client class object with an api_key in the first line of the main function. If you prefer not to put confidential information in the script, you can pass the api key with the environment variable “GEMINI_API_KEY” in your shell.

```bash
export GEMINI_API_KEY="#Put your Gemini API key here."
```

Then you can make a Client class instance without the api_key parameter in the python script.

```python
client=genai.Client()
```

After a Client instance is made, we call the generate_content method, which sends a prompt to Gemini and gets its response. The method should provided with model parameter that selects the specific Gemini model, and contents parameter that will be conveyed to Gemini as a prompt. Of course, our prompt is “Say Hello, world!”. Gemini is a trustworthy buddy. If I tell it to say “Hello, world!”, it will say so.

The response of Gemini is stored in the response instance, and its contents can be accessed by response.text. Finally, we print response.text.

Let’s find out if our program works.

```bash
python3 helloWorld.py
```

We can see that our program really prints “Hello, world!”

Now we have a bold “Hello, world!” program that uses AI. The only problem is that our script always needs an internet connection and produces much more carbon than the older program.

What can we do more?
=======

If we can use Gemini in a Python script, what else could we do? What about letting your Python script automatically trade Bitcoins, providing Gemini with live information and let it decide when to sell and buy? There must be a million ways of using Gemini in a Python script other than this silly program.

Reference
=====

1. [Gemini API docs](https://ai.google.dev/gemini-api/docs)