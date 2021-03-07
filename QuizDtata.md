
## API calls

```

### get all the quizzes
GET http://localhost:8080/api/quizzes

### get quiz by id
GET http://localhost:8080/api/quizzes/1

### create a quiz
POST http://localhost:8080/api/quizzes/create

### update a quiz
PUT http://localhost:8080/api/quizzes/1

###
DELETE http://localhost:8080/api/quizzes/6

#################################################
############### User Attempt Quiz ###############

### Get attempts by user id
GET http://localhost:8080/api/users/1/attempts

### Create an user attempt: Case 1
POST http://localhost:8080/api/users/1/attempts

### Create an user attempt: Case 2
POST http://localhost:8080/api/users/1/attempts

### Create/update an user attempt: Case 3
POST http://localhost:8080/api/users/1/attempts

### delete all the user attempts specify an user_id
DELETE http://localhost:8080/api/users/1/attempts

### Get all attempts for a quiz
GET http://localhost:8080/api/quizzes/1/attempts


```


# User Quiz Attempts API call resquest examples


### **Get** attempts by user id **[API-1001]**
GET http://localhost:8080/api/users/1/attempts 
```
GET http://localhost:8080/api/users/1/attempts

Results:

[
  {
    "id": 28,
    "user_id": 1,
    "attempt_id": 28,
    "scores": 2,
    "created_at": "2021-03-07 08:32:13",
    "updated_at": "2021-03-07 08:38:34",
    "options": null
  },
  {
    "id": 29,
    "user_id": 1,
    "attempt_id": 29,
    "scores": 0,
    "created_at": "2021-03-07 08:32:28",
    "updated_at": "2021-03-07 08:32:28",
    "options": null
  },
  {
    "id": 30,
    "user_id": 1,
    "attempt_id": 30,
    "scores": 2,
    "created_at": "2021-03-07 08:32:43",
    "updated_at": "2021-03-07 08:38:23",
    "options": null
  }
]
```

### **Create/update** user attempts
### **Case 1**: Create an user attempt record, but when no quizzes has been taken. it will return the new created attempt_id and user_attempt_id **[API-1002]**

POST http://localhost:8080/api/users/1/attempts

```
POST http://localhost:8080/api/users/1/attempts

Results:

{
  "success": true,
  "attempt_id": 31,
  "user_attempt_id": 31
}
```
### **Case 2**: Create an user attempt, together with taking the quiz (quizzes id=1 below) with all the student selected answers **[API-1003]**

Sample Request: 
```
POST http://localhost:8080/api/users/1/attempts
content-type: application/json

{
  "quiz_id": 1,
  "behavior_answers": ["Smiling"],
  "interpretation_answers": ["Happy", "sad"],
  "scores": 1
}
```

### **Case 3**: after user created an attempt to a quiz with answers, then they want to change the answer and re-submit. In this case, user_attempt_id needs to be provided as below. The user_attempt_id is come from: API-1001(the id), it id from the return record **[API-1004]**

Sample Request: 
```
POST http://localhost:8080/api/users/1/attempts
content-type: application/json

{
  "user_attempt_id": 1,
  "behavior_answers": ["Smiling"],
  "interpretation_answers": ["happy"],
  "scores": 2
}
```

### **Delete** all the user attempts specify an user_id, all the attempts including attempted quiz answers will be removed **[API-1005]** 
DELETE http://localhost:8080/api/users/1/attempts 

```
DELETE http://localhost:8080/api/users/1/attempts
```

### **Get** all attempts for a quiz (question) **[API-1006]**
GET http://localhost:8080/api/quizzes/1/attempts

```
GET http://localhost:8080/api/quizzes/1/attempts

[
  {
    "id": 15,
    "attempt_id": 30,
    "quiz_id": 1,
    "created_at": "2021-03-07 08:32:43",
    "updated_at": "2021-03-07 08:32:43"
  },
  {
    "id": 16,
    "attempt_id": 32,
    "quiz_id": 1,
    "created_at": "2021-03-07 08:42:57",
    "updated_at": "2021-03-07 08:42:57"
  }
]
```






# Quiz Creation API call resquest examples
GET http://localhost:8080/api/quizzes  result:
```
[
  {
    "id": 1,
    "code": "hour8888",
    "animal": "horse",
    "video": "https:\/\/www.youtube.com\/watch?v=8bgnG4Ni9Jo",
    "question": "Advance: Please indicate behaviors and interpretations",
    "created_at": null,
    "updated_at": "2021-02-24T05:28:51.000000Z",
    "options": null
  },
  {
    "id": 2,
    "code": "cat002",
    "animal": "cat",
    "video": "https:\/\/www.youtube.com\/watch?v=8bgnG4Ni9Jo",
    "question": "Please indicate behaviors and interpretations",
    "created_at": "2021-02-24T05:28:36.000000Z",
    "updated_at": "2021-02-24T05:28:36.000000Z",
    "options": null
  }
]
```
GET http://localhost:8080/api/quizzes/1  result:
```
{
  "id": 1,
  "code": "hour8888",
  "animal": "horse",
  "video": "https:\/\/www.youtube.com\/watch?v=8bgnG4Ni9Jo",
  "question": "Advance: Please indicate behaviors and interpretations",
  "created_at": null,
  "updated_at": "2021-02-24T05:28:51.000000Z",
  "options": null,
  "quiz_question_options": [
    {
      "id": 1,
      "quiz_question_id": 1,
      "type": "behavior",
      "title": "Kicking",
      "marking_scheme": 1,
      "is_solution": 0,
      "created_at": null,
      "updated_at": null,
      "options": null
    },
    {
      "id": 2,
      "quiz_question_id": 1,
      "type": "behavior",
      "title": "Smiling",
      "marking_scheme": 1,
      "is_solution": 1,
      "created_at": null,
      "updated_at": null,
      "options": null
    },
    {
      "id": 3,
      "quiz_question_id": 1,
      "type": "interpretation",
      "title": "Angry",
      "marking_scheme": 1,
      "is_solution": 0,
      "created_at": null,
      "updated_at": null,
      "options": null
    },
    {
      "id": 4,
      "quiz_question_id": 1,
      "type": "interpretation",
      "title": "Happy",
      "marking_scheme": 1,
      "is_solution": 1,
      "created_at": null,
      "updated_at": null,
      "options": null
    }
  ]
}

```

POST http://localhost:8080/api/quizzes/create request example
```
POST http://localhost:8080/api/quizzes/create
content-type: application/json

{
    "code": "cat002",
    "animal": "cat",
    "video": "https:\/\/www.youtube.com\/watch?v=8bgnG4Ni9Jo",
    "question": "Please indicate behaviors and interpretations",
    "quiz_question_options": [
    {
      "type": "behavior",
      "title": "Smiling",
      "marking_scheme": 1,
      "is_solution": 1,
      "created_at": null,
      "updated_at": null,
      "options": null
    },
    {
      "type": "interpretation",
      "title": "Happy",
      "marking_scheme": 1,
      "is_solution": 1,
      "created_at": null,
      "updated_at": null,
      "options": null
    },
    {
      "type": "interpretation",
      "title": "Sad",
      "marking_scheme": 1,
      "is_solution": 0,
      "created_at": null,
      "updated_at": null,
      "options": null
    }
  ]
}
```

PUT http://localhost:8080/api/quizzes/1 request example.1
```
###
PUT http://localhost:8080/api/quizzes/1 HTTP/1.1
Content-Type: application/json

{
    "code": "horse9999",
    "animal": "shire horse",
    "video": "https:\/\/www.youtube.com\/watch?v=8bgnG4Ni9Jo",
    "question": "pppPlease indicate behaviors and interpretations"
}
```
PUT http://localhost:8080/api/quizzes/1 request example.2
```
###
PUT http://localhost:8080/api/quizzes/1
content-type: application/json

{
    "code": "hour8888",
    "question": "Advance: Please indicate behaviors and interpretations",
    "quiz_question_options": [
    {
      "id": 4,
      "type": "interpretation",
      "title": "Happy"
    }]
}
```
###
DELETE http://localhost:8080/api/quizzes/6
```
###
DELETE http://localhost:8080/api/quizzes/6
```


## Testing Data for Quiz, and quiz options

```sql
INSERT INTO quiz_questions(code, animal, video, question)
 VALUES ('horse001','horse', 'https://www.youtube.com/watch?v=8bgnG4Ni9Jo', 'Please indicate behaviors and interpretations');


INSERT INTO quiz_question_options(quiz_question_id, type, title, marking_scheme, is_solution)
 VALUES 
    (1, 'behavior', 'Kicking', 1, 0 ),
    (1, 'behavior', 'Smiling',  1, 1 ),
    (1, 'interpretation', 'Angry',  1, 0), 
    (1, 'interpretation', 'Happy',  1, 1 );

select q.*, o.
 from quiz_questions q
 inner join quiz_question_options o
  on o.quiz_question_id = q.id
 where q.id=?
```

