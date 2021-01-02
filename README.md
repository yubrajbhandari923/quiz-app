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
Will be a REST API with to work as local server (to take tests in schools). or can be implemented in Internet with any SPA, desktop, or native mobile client.
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
      - Owner `Foreign Key with User Model`
      - per_question_time `in seconds, seperated wih comma if for competition and consecutive group get different time for each question, first one will be appiled for a test `
  + **`Question`**
    - set_id
    - Question_text
    - has_text_field
    - has_choices
    - has_hints
    - correct_answers `Different Possible answers seperated with commas`
    - owner
    - is_public `Anyone can add this question to their set`
    - manual_check `Automatically check correct(if FALSE) or manually check(if TRUE) `
    - mark
    - negetive_mark
  + **`Choice`**
    - question_id
    - choice_text
  + **`Hint`**
    - question_id
    - hint_text
  + **`Answer`**
    - submitted_by
    - question_id
    - answer_text
    - is_correct(METHOD) `checks answer_text with correct_answers`
  + **`Competition`**
    For conducting quiz competiton
    - master_question_set_id
    - title
    - description
    - organizer
    - additional text
  + **`Group`**
    - competition_id
    - group_name
    - members `Comma Seperated names`
    - additional_info
  + **`CompetitionAnswer`**
    - group_id
    - question_id
    - is_correct
    
    
    
### Authentication System
**Model:** `django.contrib.auth.models.User`
+ Authentication System is handled with JWT Tokens.  
+ Refresh Token (15 days Valid) as HttpOnly Cookie and Access Token as Json will be provided on authentication.  
+ Must create account to create questionnair or submit answers.
