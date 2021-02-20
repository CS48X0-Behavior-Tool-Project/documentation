



## API calls

```

### get all the quizzes
GET http://localhost:8080/api/quizzes

### get quiz by id
GET http://localhost:8080/api/quizzes/1

```


## API call resquest examples
GET http://localhost:8080/api/quizzes
```
[
  {
    "id": 1,
    "code": "horse001",
    "video": "https:\/\/www.youtube.com\/watch?v=8bgnG4Ni9Jo",
    "question": "Please indicate behaviors and interpretations",
    "created_at": null,
    "updated_at": null,
    "options": null
  }
]
```
GET http://localhost:8080/api/quizzes/1
```
{
  "id": 1,
  "code": "horse001",
  "video": "https:\/\/www.youtube.com\/watch?v=8bgnG4Ni9Jo",
  "question": "Please indicate behaviors and interpretations",
  "created_at": null,
  "updated_at": null,
  "options": null,
  "quiz_question_options": [
    {
      "id": 1,
      "quiz_question_id": 1,
      "type": "behavior",
      "title": "Kicking",
      "marking_scheme": "1",
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
      "marking_scheme": "1",
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
      "marking_scheme": "1",
      "is_solution": 0,
      "created_at": null,
      "updated_at": null,
      "options": null
    },
    {
      "id": 4,
      "quiz_question_id": 1,
      "type": "interpretation",
      "title": "Happ",
      "marking_scheme": "1",
      "is_solution": 1,
      "created_at": null,
      "updated_at": null,
      "options": null
    }
  ]
}

```

## Testing Data for Quiz, and quiz options

```sql
INSERT INTO quiz_questions(code, video, question)
 VALUES ('horse001', 'https://www.youtube.com/watch?v=8bgnG4Ni9Jo', 'Please indicate behaviors and interpretations')


INSERT INTO quiz_question_options(quiz_question_id, type, title, marking_scheme, is_solution)
 VALUES 
    (1, 'behavior', 'Kicking', 1, 0 ),
    (1, 'behavior', 'Smiling',  1, 1 ),
    (1, 'interpretation', 'Angry',  1, 0), 
    (1, 'interpretation', 'Happ',  1, 1 );

select q.*, o.
 from quiz_questions q
 inner join quiz_question_options o
  on o.quiz_question_id = q.id
 where q.id=?
```
