# Typing Speed Game

## Project Overview

Welcome to the Typing Speed Game! This application is designed to test and improve your typing speed by challenging you to type displayed words correctly within a limited time frame. The game is developed using Python and Tkinter for the graphical user interface.

## Table of Contents

1. [Project Description](#project-description)
2. [Technologies Used](#technologies-used)
3. [Setup and Installation](#setup-and-installation)
4. [Usage](#usage)
5. [Code Explanation](#code-explanation)
6. [Project Structure](#project-structure)
7. [Contributing](#contributing)
8. [License](#license)
9. [Contact](#contact)

## Project Description

The Typing Speed Game aims to help users improve their typing skills by providing a fun and interactive platform. The game displays random words that the user must type correctly. The user's score is tracked based on the number of correct entries, and the typing speed is calculated in letters per second.

### Features

- Display of random words for the user to type.
- Real-time score and time tracking.
- Calculation of typing speed in letters per second.
- Option to retry the game after it ends.

## Technologies Used

- **Python**: Primary programming language used for development.
- **Tkinter**: Library used for creating the graphical user interface.

## Setup and Installation

### Prerequisites

Ensure you have the following installed:

- Python (version 3.6 or higher)

### Installation Steps

1. **Clone the Repository**

   ```bash
   git clone https://github.com/username/TypingSpeedGame.git
   cd TypingSpeedGame
   ```

2. **Run the Game**

   ```bash
   python typing_speed_game.py
   ```

## Usage

### Starting the Game

1. Run the script `typing_speed_game.py`.
2. The game window will open with a welcome message.
3. Press `Enter` to start the game.

### Playing the Game

1. A random word will be displayed in the center of the screen.
2. Type the word in the input box and press `Enter`.
3. If the word is typed correctly, the score will increase.
4. If the word is typed incorrectly, the miss count will increase.
5. The game will continue for 60 seconds, after which the final score and typing speed will be displayed.
6. You can choose to retry the game by clicking the retry button in the dialog box.

## Code Explanation

### Main Functions

#### `labelSlider()`

Displays a welcome message in a sliding manner.

```python
def labelSlider():
    global count, sliderwords, speed
    text = "Welcome to typing Speed Game"

    if count >= len(text):
        count = 0
        sliderwords = ''
    sliderwords += text[count]
    count += 1
    fontLabel.configure(text=sliderwords)
    fontLabel.after(150, labelSlider)
```

#### `time()`

Handles the countdown timer and calculates typing speed.

```python
def time():
    global timeleft, score, miss, speed, total
    if timeleft >= 12:
        pass
    else:
        timeLabelCount.configure(fg='red')
    if timeleft > 0:
        timeleft -= 1
        timeLabelCount.configure(text=timeleft)
        timeLabelCount.after(1000, time)
        if timeleft == 0:
            speed = speed.join(letter)
            total = ((len(speed)) / 60)
            print('Typing Speed is', math.ceil(total), 'letter/sec')
    else:
        gamePlayDetailLabel.configure(text='Hit = {} | Miss = {} | Total Score = {}'.format(score, miss, score - miss))
        speedperseclLabel.configure(text='Typing Speed in letter/sec = {}'.format(math.ceil(total)))
        rr = messagebox.askretrycancel('Notification', 'Play Again Hit Retry Button')
        if rr == True:
            score = 0
            timeleft = 60
            miss = 0
            timeLabelCount.configure(text=timeleft)
            wordLabel.configure(text=words[0])
            scoreLabelCount.configure(text=score)
```

#### `startGame(event)`

Starts the game and handles user input.

```python
def startGame(event):
    global score, miss, speed
    if timeleft == 60:
        time()
    gamePlayDetailLabel.configure(text='')
    if wordEntry.get() == wordLabel['text']:
        score += 1
        scoreLabelCount.configure(text=score)
        letter.append(wordEntry.get())
    else:
        miss += 1
    random.shuffle(words)
    wordLabel.configure(text=words[0])
    wordEntry.delete(0, END)
```

### UI Elements

#### Labels

```python
fontLabel = Label(root, text=" ", font=("arial", 25, "italic bold"), bg="powder blue", fg="red", width=40)
fontLabel.place(x=10, y=10)
labelSlider()

wordLabel = Label(root, text=words[0], font=("arial", 40, "italic bold"), bg='powder blue')
wordLabel.place(x=350, y=200)

scoreLabel = Label(root, text="Your Score :", font=("arial", 25, "italic bold"), bg="powder blue")
scoreLabel.place(x=10, y=100)

scoreLabelCount = Label(root, text=score, font=("arial", 25, "italic bold"), bg="powder blue", fg='blue')
scoreLabelCount.place(x=80, y=180)

timerCount = Label(root, text="Time Left :", font=("arial", 25, "italic bold"), bg="powder blue")
timerCount.place(x=600, y=100)

timeLabelCount = Label(root, text=timeleft, font=("arial", 25, "italic bold"), bg="powder blue", fg='blue')
timeLabelCount.place(x=680, y=180)

gamePlayDetailLabel = Label(root, text="Type Word and Hit Button", font=("arial", 20, "italic bold"), bg="powder blue", fg='violet red')
gamePlayDetailLabel.place(x=180, y=450)

speedperseclLabel = Label(root, font=("arial", 35, "italic bold"), bg="powder blue", fg='red')
speedperseclLabel.place(x=85, y=480)
```

#### Entry

```python
wordEntry = Entry(root, font=("arial", 25, "italic bold"), bd=10, justify="center")
wordEntry.place(x=250, y=300)
wordEntry.focus_set()
```

## Project Structure

```
TypingSpeedGame/
├── typing_speed_game.py
├── README.md
```

## Contributing

Contributions are welcome! Please follow these steps:

1. Fork the repository.
2. Create a new branch (`git checkout -b feature/your-feature`).
3. Commit your changes (`git commit -m 'Add some feature'`).
4. Push to the branch (`git push origin feature/your-feature`).
5. Open a Pull Request.

## License

This project is licensed under the MIT License. See the `LICENSE` file for more details.

## Contact

-**Saumya Poojari** - [saumya.poojarii7@gmail.com]

-LinkedIn - https://www.linkedin.com/in/ssaumz/

Feel free to reach out with any questions or feedback!

---

Thank you for your interest in the Typing Speed Game project. Happy coding! 🚀
