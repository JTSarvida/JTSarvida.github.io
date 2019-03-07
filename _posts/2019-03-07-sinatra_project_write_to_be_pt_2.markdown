---
layout: post
title:      "Sinatra Project: Write to Be pt. 2"
date:       2019-03-07 20:07:45 +0000
permalink:  sinatra_project_write_to_be_pt_2
---


Hello! So, I have finally completed my Sinatra project, and want to share it with you all! In regards to the basic requirements of the project, there wasn't too much difficulty. However, this being my second portfolio project, I wanted to surpass these basic requirements. My attempt at this was to focus on the actual presentation of the project itself. The main thing I want to highlight in this attempt would be my use of modals instead of flash messages. Modals are pop up boxes that display over the main content of the page momentarily when certain conditions are met. In this case, modals would display when logging in, editing/deleting affirmations, when fields were blank, or when field inputs were not incorrect. This proved to be difficult, but is functional and I'm excited with how it turned out! Now, without further delay, here's my project! It can also be found on https://github.com/JTSarvida/Write-to-be-2

## Write to Be:

### Welcome Page:

![](https://i.imgur.com/qj46L54.png?2)

This welcome page shows an about section for the website, explaining what exactly is Write to Be. Underneath this is a register and log in link.

### Log In Page (Registration page looks the same, just replace the words with Register):

![](https://i.imgur.com/qoHGwHX.png?1)

Here is a log in page that asks for a user's info that they registered under. In our case, this is Username, Email Address, and Password.  Once the user puts in the info, a flash message will show if the appropriate fields were incorrectly filled or left blank. The intent is to update this later with a modal instead of a flash message, which is what I did in later uses of validation messages.

### A User's Home Page:

![](https://i.imgur.com/I2fGt3Y.png?1)

This is the user's home page, which shows multiple things. When looking at the top left corner, you see a the user's profile box which gives them several options. In this area, you can choose to view your written affirmations, view all of the affirmations, and also create a new affirmation. In the middle of the page you can see 10 affirmations of the day. In the future, I want to make sure that these affirmations are random. I believe I had them set to randomize, but I think this only happens the first time, not for each time you log in. You can click on any of these affirmations and be directed to that affirmation's page, which will be shown later.

### A User's Affirmations Page:

![](https://i.imgur.com/zCqPtdc.png?1)

This is a page that displays all the affirmations that the user has written. Just like the daily affirmation section, you can click on any of these affirmations to be directed to that respective affirmation's page.

### Affirmation Index Page:

![](https://i.imgur.com/HVIb5UX.png?1)

On this page, you see every affirmation that was written, regardless of creator.

### Single Affirmation Page:

![](https://i.imgur.com/Z3SMpMF.png?1)

On this page, you can see the affirmation, it's creator, and two options below: edit and delete. A modal with the appropriate message will pop up when hitting either of these buttons. If you aren't the affirmation's creator, a modal saying "You cannot edit or delete another user's affirmation" when hitting these buttons. The modal will say "Editing the affirmation!" or "Deleting the affirmation!" if you are the appropriate user.



I learned a lot from this project and hope to continue adding onto it in the future.
