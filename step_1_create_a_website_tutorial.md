Step 1. Tell the website requirment
```
I want to build a trivia-like game with Flask. Each page should have a question and an expected answer. The person then has a slider to predict the probability they believe GPT4 will answer the question with the expected answer. There should be a submit button on each page. When they click submit, it should show whether or not GPT-4 could actually answer the question (and give the answer the model gave as a reference). Then there should be a "Next Question" button.


I want the following pages
- GET /home: introduce the contest. Explain the rules. Have a single link to start with the first question. Create a session variable for this person.
- GET /question?id=[uuid]: show question [uuid] as described above
- POST /score: given POST parameters id=[uuid] session=[uuid] and guess=[float from 0 to 1]
* First add this guess to the list of all guesses for that question
* Then compute the person's log loss to return
* Finally say how well this is compared to everyone else on that question.


You will need global variables for
- scores: a dictionary mapping question UUID to a list of predictions as floats. {question1: [.5, .1, .9]}
- entries: a dictionary mapping user UUIDs to a dictionary of question UUIDs to floats. So for example {person1: {question1: .5, question2: .8}}
- questions: a list of tuples of Q/A pairs: [("What is 1+1?", "2")...]
- answers: a list of integers for whether or not the model gets it right [0, 1, 0 ...]
```