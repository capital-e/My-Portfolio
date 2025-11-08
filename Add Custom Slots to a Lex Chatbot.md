<img src="https://cdn.prod.website-files.com/677c400686e724409a5a7409/6790ad949cf622dc8dcd9fe4_nextwork-logo-leather.svg" alt="NextWork" width="300" />

# Add Custom Slots to a Lex Chatbot

**Project Link:** [View Project](http://learn.nextwork.org/projects/aws-ai-lex2)

**Author:** Jonathan Nutsugah  
**Email:** nutsugahjonathan@gmail.com

---

## Add Custom Slots to a Lex Chatbot

![Image](http://learn.nextwork.org/amused_pink_zesty_alpaca/uploads/aws-ai-lex2_c4fc89af)

---

## Introducing Today's Project!

I used Amazon Lex to set up a new intent with custom slots so BankerBot can gather user details like account type and birthday to check balances.

### What is Amazon Lex?

Amazon Lex is an AWS service for building chatbots that understand natural language through text or voice.

### One thing I didn't expect in this project was...

I didn’t expect how easily Lex could capture slot values directly from a user’s sentence without extra prompts.

### This project took me...

This project took me about an hour to complete.

---

## Slots

Slots are details the bot asks for and stores, like blanks in a form, to complete a user’s request.

It means users can give specific details, like account type, and the bot will understand and respond accurately.

I set up a custom slot type so BankerBot only recognizes valid account types—Checking, Savings, and Credit—and avoids invalid inputs.

![Image](http://learn.nextwork.org/amused_pink_zesty_alpaca/uploads/aws-ai-lex2_97dc2351)

---

## Connecting slots with intents

It means the bot will only accept the specific values I defined and ignore any others.

The CheckBalance intent collects a user’s account type and date of birth so the bot can verify details before showing the balance.

![Image](http://learn.nextwork.org/amused_pink_zesty_alpaca/uploads/aws-ai-lex2_c4fc89af)

---

## Slot values in utterances

I added placeholders like {accountType} in the utterances so Lex can capture the slot value directly from the user’s input.

![Image](http://learn.nextwork.org/amused_pink_zesty_alpaca/uploads/aws-ai-lex2_505be5b8)

---

## Handling failures in slot values

---

---
