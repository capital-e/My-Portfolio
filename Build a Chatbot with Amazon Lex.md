<img src="https://cdn.prod.website-files.com/677c400686e724409a5a7409/6790ad949cf622dc8dcd9fe4_nextwork-logo-leather.svg" alt="NextWork" width="300" />

# Build a Chatbot with Amazon Lex

**Project Link:** [View Project](http://learn.nextwork.org/projects/aws-ai-lex1)

**Author:** Jonathan Nutsugah  
**Email:** nutsugahjonathan@gmail.com

---

## Build a Chatbot with Amazon Lex

![Image](http://learn.nextwork.org/amused_pink_zesty_alpaca/uploads/aws-ai-lex1_505be5b8)

---

## Introducing Today's Project!

### What is Amazon Lex?

Amazon Lex is an AWS service for building chatbots that understand natural language through text or voice.

### How I used Amazon Lex in this project

I learned about Amazon Lex, intents, utterances, FallbackIntent, session timeouts, and the intent confidence score threshold.

### One thing I didn't expect was...

I was surprised by how quickly I could build a working chatbot and how well Lex recognized variations of user inputs.

### This project took me...

It took me less than an hour to complete the project.

---

## Setting up a Lex chatbot

It took just a few minutes to set up the basic chatbot structure.

I gave it basic Amazon Lex permissions so it can call other AWS services, like Lambda, on my behalf.

It’s the minimum confidence level Lex needs to correctly understand what the user is asking before giving a response.

![Image](http://learn.nextwork.org/amused_pink_zesty_alpaca/uploads/aws-ai-lex1_97dc2351)

---

## Intents

Intents are the goals or actions a user wants to achieve when chatting with the bot, like checking a balance or saying hello.

WelcomeIntent recognizes greetings from users and responds with a friendly welcome message.

![Image](http://learn.nextwork.org/amused_pink_zesty_alpaca/uploads/aws-ai-lex1_505be5b8)

---

## FallbackIntent

It understood “Hi,” “Hello,” “I need help,” and “Can you help me?”

It returned an error when the input didn’t match any defined intent, like “how are you”

![Image](http://learn.nextwork.org/amused_pink_zesty_alpaca/uploads/aws-ai-lex1_505be5b8)

---

## Configuring FallbackIntent

FallbackIntent is triggered when the bot’s confidence in matching a user’s input to an intent falls below the set threshold.

I configured FallbackIntent to give clearer, user-friendly messages and guide users on what the bot can do.

---

## Variations

I changed the default message to a clearer one, added helpful hints, and created variations so responses feel more natural.

I also added variations! Variations are different versions of a response that Lex can randomly use to make the bot sound more natural and conversational.

![Image](http://learn.nextwork.org/amused_pink_zesty_alpaca/uploads/aws-ai-lex1_c4fc89af)

---

## Initial Responses

---

---
