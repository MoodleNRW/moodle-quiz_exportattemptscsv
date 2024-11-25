# moodle-quiz-exportattemptscsv
A Quiz report plugin for Moodle to export the attempts history as a [CSV](https://en.wikipedia.org/wiki/Comma-separated_values) file

With this plugin every teacher should be able to export the attempts history of a quiz with a plenty of details directly in [CSV](https://en.wikipedia.org/wiki/Comma-separated_values) format.
The aim of this plugin is to let each teacher to analyze quiz attempts data with their personal tools, like a spreadsheet or other more powerful tools.

Normally Moodle let the teacher to show the attempt history of a single studente at a time and the information on the attempt could not be downloaded: with this plugin the teacher will have a new optional report named "Export Attempts history as CSV" in the "results" quiz administration menu.
The teacher will have some options on which information will be available into the file download (e.g question text, response, right answer or personal information) then selecting the students and clicking on "show report" the collected information will be downloaded to the teacher's computer.

Obviously, the report information could be critical data from privacy point of view, so teachers should be aware that the downloaded data should be adequately protected from stealing.


# Table of Content

| Exportfield Name                       | Tabel                      | Column          | Referenz to | Description                                                                                                                                                    |
| -------------------------------------- | -------------------------- | --------------- | ----------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Nr.                                    | \-                         | \-              | \-          | Squentially number of exported data.                                                                                                                           |
| User ID                                | quiz_attempts              | userid          | user.id     | Foreign key reference to the user whose attempt this is.                                                                                                       |
| Test ID                                | quiz_attempts              | quiz            | quiz.id     | Foreign key reference to the quiz that was attempted.                                                                                                          |
| Versuch-ID                             | quiz_attempts              | id              | \-          | Primary key of the attempts table                                                                                                                              |
| Versuch Nr.                            | quiz_attempts              | attempt         | \-          | Sequentially numbers this student’s attempts at this quiz.                                                                                                     |
| Summiert Bewertungen des Versuchs      | quiz_attempts              | sumgrades       | \-          | Total marks for this attempt.                                                                                                                                  |
| Frageslot des Versuchs                 | question_attempts          | slot            | \-          | Used to number the questions in one attempt sequentially.                                                                                                      |
| Frage-ID                               | question_attempts          | questionid      | question.id | The id of the question being attempted. Foreign key references.                                                                                                |
| Fragevariante                          | question_attempts          | variant         | \-          | The variant of the qusetion being used.                                                                                                                        |
| Maximale Punkte für die Frage          | question_attempts          | maxmark         | \-          | The grade this question is marked out of in this attempt.                                                                                                      |
| Kleinster Teilwert für die Frage       | question_attempts          | minfraction     | \-          | Some questions can award negative marks. This indicates the most negative mark that can be awarded, on the faction scale where the maximum positive mark is 1. |
| Versuch markiert                       | question_attempts          | flagged         | \-          | Whether this question has been flagged within the attempt.                                                                                                     |
| Nr. des Fragenversuchsschritts         | question_attempt_steps     | sequencenumber  | \-          | Numbers the steps in a question attempt sequentially.                                                                                                          |
| Status des Fragenversuchsschritts      | question_attempt_steps     | state           | \-          | One of the constants defined by the question_state class, giving the state of the question at the end of this step.                                            |
| Teilwert für den Fragenversuchsschritt | question_attempt_steps     | fraction        | \-          | The grade for this question, when graded out of 1. Needs to be multiplied by question_attempt.maxmark to get the actual mark for the question.                 |
| Zeitstempel des Fragenversuchsschritts | question_attempt_steps     | timecreated     | \-          | Time-stamp of the action that lead to this state being created.                                                                                                |
| Korrekte Antwort des Versuchs          | question_attempts          | rightanswer     | \-          | This is a human-readable textual summary of the right answer to this question.                                                                                 |
| Fragetext                              | question_attempts          | questionsummary | \-          | This is a textual summary of the question the student has to answer.                                                                                           |
| Antwort des Versuchs                   | question_attempts          | responsesummary | \-          | This is a textual summary of the student’s response (basically what you would expect to in the Quiz responses report).                                         |
| Name des Fragenversuchsschritts        | question_attempt_step_data | name            | \-          | The name of this bit of data.                                                                                                                                  |
| Attempt step value                     | question_attempt_step_data | value           | \-          | The corresponding value                                                                                                                                        |
| -------------------------------------- | -------------------------- | --------------- | ----------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------- |


## Installation and set-up

This plugin should be compatible with Moodle 3.11+

### Install using git

Or you can install using git. Type this commands in the root of your Moodle install

    git clone https://github.com/MoodleNRW/moodle-quiz_exportattemptscsv.git mod/quiz/report/exportattemptscsv
    echo '/mod/quiz/report/exportattemptscsv/' >> .git/info/exclude
    
Then run the moodle update process
Site administration > Notifications
