
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
```


## API call resquest examples
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
