# Full Stack Bonding Experience API Project

## Introduction

This is a Bonding experiences application for employees and students. A bunch of team members got the idea to hold Bonding Experience on a regular basis and created a webpage to manage the Bonding Experience app and play the game, but their API experience is limited and still needs to be built out.

That's where you come in! Help them finish the Bonding Experience app so they can start holding Bonding Experience and seeing who's the most knowledgeable of the bunch. The application must:

## Tech Stac(Dependencies)

### PIP Dependencies

- **Python 3.7**
- **Virtual Enviornment**
- **SQLAlchemy** ORM to be our ORM library of choice
- **PostgreSQL** as our database of choice
- **Python3** and **Flask** as our server language and server framework
- **Flask-Migrate** for creating and
  running schema migrations

Once the virtual environment setup and running, then the dependencies can be install by naviging to the /backend directory and the following command should be run:
`pip install -r requirements.txt`

This will install all the reuired packages that I have selecteed within the requirements.txt file.

## Main Files: Project Structure

├── README.md
├── [backend]
| ├── flaskr
| | ├── **init**.py \*\*\_ the main driver of the app.
| |  
| ├── models.py
| ├── README.md
| ├── requirements.txt
| ├── test_flaskr.py
| ├── trivia.psql
| |**\_
├── [frontend]
├── public
├── src
├── README.md
|**

## Database Setup

With Postgres running,restore the database.

`psql trivia < trivia.psql`

**Running the server**
In the backend directory, execute:

```
set FLASK_APP=myapp
set FLASK_ENV=development # enables debug mode
python3 app.py
```

## API

GET `\categories` Fetches a dictionary of all available categories

Request parameters: none
Example response:

```
{
  "categories": {
    "1": "Science",
    "2": "Art",
    "3": "Geography",
    "4": "History",
    "5": "Entertainment",
    "6": "Sports"
  },
  "success": true
}
```

GET `\questions?page=<page_number>` Fetches a paginated dictionary of questions of all available categories

Request parameters (optional): page:int
Example response:

```
 "categories": {
   "1": "Science",
   "2": "Art",
   "3": "Geography",
   "4": "History",
   "5": "Entertainment",
   "6": "Sports"
 },
 "current_category": null,
 "questions": [
   {
     "answer": "Maya Angelou",
     "category": 4,
     "difficulty": 2,
     "id": 5,
     "question": "Whose autobiography is entitled 'I Know Why the Caged Bird Sings'?"
   },
   {
     "answer": "Escher",
     "category": 2,
     "difficulty": 1,
     "id": 16,
     "question": "Which Dutch graphic artist\u2013initials M C was a creator of optical illusions?"
   }
 ],
 "success": true,
 "total_questions": 2
}

```

DELETE `/questions/<question_id>` Delete an existing questions from the repository of available questions

Request arguments: question_id:int
Example response:

```
{
  "deleted": "28",
  "success": true
}
```

POST `/questions` Add a new question to the repository of available questions

Request body: {question:string, answer:string, difficulty:int, category:string}
Example response:

```
{
  "created": 29,
  "success": true
}

```

POST `/questions/search` Fetches all questions where a substring matches the search term (not case-sensitive)

Request body: {searchTerm:string}
Example response:

```
{
  "current_category": null,
  "questions": [
    {
      "answer": "Lisbon",
      "category": 2,
      "difficulty": 1,
      "id": 29,
      "question": "What is the capital of Portugal?"
    }
  ],
  "success": true,
  "total_questions": 1
}

```

GET `/categories/<int:category_id>/questions` Fetches a dictionary of questions for the specified category

Request argument: category_id:int
Example response:

```
{
  "current_category": 1,
  "questions": [
    {
      "answer": "The Liver",
      "category": 1,
      "difficulty": 4,
      "id": 20,
      "question": "What is the heaviest organ in the human body?"
    },
    {
      "answer": "Alexander Fleming",
      "category": 1,
      "difficulty": 3,
      "id": 21,
      "question": "Who discovered penicillin?"
    },
  ],
  "success": true,
  "total_questions": 2
}

```

POST `/quizzes` Fetches one random question within a specified category. Previously asked questions are not asked again.

Request body: {previous_questions: arr, quiz_category: {id:int, type:string}}
Example response:

```
{
  "question": {
    "answer": "The Liver",
    "category": 1,
    "difficulty": 4,
    "id": 20,
    "question": "What is the heaviest organ in the human body?"
  },
  "success": true
}

```

## Testing

To run the tests, run

```
dropdb trivia_test
createdb trivia_test
psql trivia_test < trivia.psql
python test_flaskr.py
```
