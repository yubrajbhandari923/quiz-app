# Quiz App 

This document is created for the aid of any developer who may join during the development and also for my own future references to API and other stuffs(writing my ideas down).
<br> **Created with :sparkling_heart:**

**IMPORTANT: Keep the commit messages short and informative.Proper Commit Convention may be updated in future. Read this [Article at freeCodeCamp](https://www.freecodecamp.org/news/writing-good-commit-messages-a-practical-guide/) and also try to follow this [Emoji Convention](https://gist.github.com/parmentf/035de27d6ed1dce0b36a)**

## Setup Process

**Requirements**
  - Docker
  - docker-compose
  
**Commands**
`docker-compose up`

## Backend
**Dependencies** 
  - Django
  - django_rest_framework
  - djangorestframework-simplejwt
  
 
### Models Overview
**NOTE: Use CamelCase for model name and snake_case for fields name**
  + **`django.contrib.auth.models.User`**
    Used for the mainly for authentication purposes, OnetoOne extended with `Profile` model. Stores 
    - First Name
    - Last Name
    - Username
    - Email
    - Password
  + **`Profile`**
    Stores additional informations about individual user mainly to be viewed in profile:
     - Picture
     - Institution
     - Facebook Profile
     - LinkedIn Profile
     - Additional Information `Bio type discription to show on Member Profile`
  + **`Question Set`**
    It is collection of questions.
      - Name
      - Description
      - Parent_set `Foreign key with itself`
  + **`Question`**
    - 
    
### Authentication System
**Model:** `django.contrib.auth.models.User`
+ Authentication System is handled with JWT Tokens.  
+ Refresh Token (15 days Valid) as HttpOnly Cookie and Access Token as Json will be provided on authentication.  

