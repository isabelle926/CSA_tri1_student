---
toc: true
comments: true
layout: post
title: Debugging Session 
description: Practice debugging the backend of 2nd Trimester project
type: plans
courses: { csa: {week: 25} }
---

## General Debugging:
Frontend on localhost
<img width="1309" alt="Screen Shot 2024-03-08 at 12 13 50 AM" src="https://github.com/isabelle926/CSA_tri1_student/assets/70926137/31bfe64a-ef5c-49b2-9a13-f4de3efa8d77">

Backend on localhost port 8020
<img width="1309" alt="Screen Shot 2024-03-08 at 12 14 41 AM" src="https://github.com/isabelle926/CSA_tri1_student/assets/70926137/e5cbc8a1-ef15-46b4-ad37-380bc7f519de">

When the backend is not running, the website will display the following error: 
<img width="1309" alt="Screen Shot 2024-03-08 at 12 15 57 AM" src="https://github.com/isabelle926/CSA_tri1_student/assets/70926137/0d481d82-a1fe-44e9-ac04-397cbe01ee0e">

Adding breakpoints
<img width="1309" alt="Screen Shot 2024-03-08 at 12 18 21 AM" src="https://github.com/isabelle926/CSA_tri1_student/assets/70926137/66d3f30b-d10d-4704-a0b3-af39214cbaf0">

When there is no cross origin request for the correct url, the following error will show up instead: 
<img width="1309" alt="Screen Shot 2024-03-08 at 12 18 21 AM" src="https://github.com/isabelle926/CSA_tri1_student/assets/70926137/78ea9021c-daad-7831-ac31-ae16729cedb2">

## Specific issue
I was having an issue with the login functionality. For a little context, users should only be able to access the interview page once they are logged into the website. However, while users could click the login button and access the interview page, they wouldn't actually be "logged in" and thus would be unable to start any video calls. To debug this, I first ran our backend repository on localhost:
<img width="1136" alt="Screen Shot 2024-03-05 at 12 09 19 PM" src="https://github.com/isabelle926/CSA_tri1_student/assets/70926137/7d2fd9c1-f4d7-4e46-9fb2-4419af4adb0d">

Next, I added breakpoints on UserController.java to test the register function so that I could see if new users were being created in the first place. 
<img width="1136" alt="Screen Shot 2024-03-07 at 11 39 31 AM" src="https://github.com/isabelle926/CSA_tri1_student/assets/70926137/049b3579-f812-4343-a186-9be67e0296d1">

Testing the register functionality on our frontend website, and there seems to be an error
<img width="1422" alt="Screen Shot 2024-03-08 at 12 10 16 AM" src="https://github.com/isabelle926/CSA_tri1_student/assets/70926137/726e8eee-39bb-46bd-973e-7563f4c1b486">

When I go back to vscode to check what happened, I get the following issue: 
<img width="643" alt="Screen Shot 2024-03-07 at 12 15 38 PM" src="https://github.com/isabelle926/CSA_tri1_student/assets/70926137/7d44d50f-c656-4d75-81ec-0bbc0d547799">

For some reason, the 'GET' function doesn't seem to be working. Let's see what shows up on the localhost backend website: 
<img width="1422" alt="Screen Shot 2024-03-07 at 12 19 01 PM" src="https://github.com/isabelle926/CSA_tri1_student/assets/70926137/7131e871-ddf5-4425-b435-655b367375ec">


