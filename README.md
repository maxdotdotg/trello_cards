# add_card
Take user input to add a Trello card with labels and a comment to the specified column of the board.

## Requirements
This is written in Python 3 and has one 3rd-party dependency, `requests`. Use your python environment management tool of choice to set up (I like `virtualenv`), then install the dependencies: `pip install -r requirements.txt`

`add_card` also uses a json config file for access to the [Trello API key and Server Token](https://trello.com/app-key), which looks like this:
``` bash
{
  "key": "TRELLO_API_KEY",
  "token": "TRELLO_SERVER_TOKEN"
}
```

## Usage
Here's a sample execution:
``` bash
./add_card --board "my first trello board" \
    --column "To Do" \
    --name "Cool Idea 1" \
    --comment "it sure is cool but it needs some work" \
    --label "needs work"
```

Here's the full help:

``` bash
usage: add_card [-h] --name NAME [NAME ...] --board BOARD [BOARD ...] --column
                COLUMN [COLUMN ...] [--comment COMMENT [COMMENT ...]]
                [--label LABEL [LABEL ...]] [--config CONFIG]

add a card to a trello board

optional arguments:
  -h, --help            show this help message and exit
  --name NAME [NAME ...], -n NAME [NAME ...]
                        name the card, please use double-quotes, or only the
                        first word will get used!
  --board BOARD [BOARD ...], -b BOARD [BOARD ...]
                        board the card should be added to, please use double-
                        quotes, or only the first word will get used!
  --column COLUMN [COLUMN ...], -o COLUMN [COLUMN ...]
                        column the card should be added to, please use double-
                        quotes, or only the first word will get used!
  --comment COMMENT [COMMENT ...], -c COMMENT [COMMENT ...]
                        comment to leave on the card, please use double-
                        quotes, or only the first word will get used!
  --label LABEL [LABEL ...], -l LABEL [LABEL ...]
                        label to assigned to the card, please use double-
                        quotes, or only the first word will get used!
  --config CONFIG, -f CONFIG
                        config file, defaults to ./config.json
```
