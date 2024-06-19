# Anki-Multiple-Selection

## Introduction
This is a fork of [ale18V/Anki-Multiple-Choice](https://github.com/ale18V/Anki-Multiple-Choice) that aims to support **multiple selection questions** with an arbitrary number of choices (therefore buttons) and answers.

This project is a mix of html, css and javascript that you can add to whichever note type you want and will implement the feature of multiple choices. \
It randomizes the choices every time you review your card in order to prevent you from memorizing the position of the correct choice.

## How to use
### Setup the note type
#### Creating fields
In the "Manage Note Types" window *(Ctrl+Shift+N)*, pick a note type you want to turn into multiple choice (e.g. "Basic" note type), and click the "Fields" button. \
Add two fields named "Choices" and "Answer" to the note type (without the quotes), so that it contains four fields with the names of "Front", "Back", "Choices" and "Answer" correspondingly.

#### Setting up cards
In the previous "Manage Note Types" window, click the "Cards" button. \
Then copy the content of "Front Template.html" into the Front Template box, the same thing also goes for the Back Template box and the Styling box. Then save.

### Create a card
The text inside the "Choices" field has to follow a specific format: each choice must either be on a separate line[^1] or separated by exactly one empty line[^2]. The text inside the "Answer" field follows the format below:
```
// You can manually separate values with '<br>', or don't use them at all to insert them automatically between characters.
// This also means that except for single digit numbers, manually separating the values from each other is required.
// Examples of valid input: 'aBC456', '12<br>13<br>14', yielding [0, 1, 2, 3, 4, 5] and [11, 12, 13].
```
[^1]: More specifically they should be `<br>` or `</br>` separated (the latter one is automatically replaced by the first one by this template). By default Anki adds the `<br>` tag when you add a new line, but things might go wrong if you, for example, paste text from a webpage. You can check whether the choices follow the right format using Anki's HTML inspector.
[^2]: So that in raw HTML, each choice is separated by `<br><br>`. This also means that two adjacent `<br>`s will cause what you expect to be one whole choice to become two.

### Using the template
The number of buttons are the same as the number of choices you provided.

For cards with only one correct answer, the behavior is the same as the original repository, except for that the number of buttons is not limited to 4.

A "Submit" button will appear below the choice buttons if there are more than one correct answer, this is the multiple selection mode. Choices you selected correctly will be marked green, correct choices you missed are orange, and incorrect choices you selected are red.

## Debug
Both front.html and back.html include the line: `<p id="multiple-choice-debug"></p>`. \
In case something goes wrong, a specific error message will be displayed in there.
You can delete it if you want, though I would advise keeping it, as it will always be invisible unless an error occurs.

## Contributing
If you feel like the available templates are missing some features, feel free to improve on them or share your own template by making a pull request.

Otherwise, if you have created a beautiful note type using this library, you may share it here so that others can use it as well.
