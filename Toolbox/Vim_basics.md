# VIM_cheatsheet

## Start Vim from the terminal
```vim FILENAME```

## How to move the cursor
Left : ```H```
Down : ```J```
Up : ```K```
Right : ```L```

## How to exit Vim
```:q! [ENTER]```

/!/ Doesn't save changes

## Delete characters
```X```
When done: press ```ECHAP```

## Delete a word
Go to the first character of the word and press: ```dw```
When done: press ```ECHAP```

## Delete to the end of the line
Go to the end of the correct line and press: ```d$```
When done: press ```ECHAP```

## Delete a whole line
Go to the line you want to delete: ```dd```

## Insert characters
```I```
When done: press ```ECHAP```

## Edit a file
Save a file and quit: ```:wq``` ou ```:x```

## Go back to beginning of a line
```0```

## Undo a command
```u```

## Redo a command
```CTRL + R```

## The PUT command
To put previously deleted text where the cursor is: ```p```

## Copy/paste text
Place the cursor where you want to copy and start visual mode: ```v```
To copy: ```y```
To paste: ```p```

## Execute external command
```:! COMMAND [ENTER]```
