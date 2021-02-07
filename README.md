# add_card
Take user input to add a Trello card with labels and a comment to the specified column of the board.

## Requirements
This is written in Python 3 and has one 3rd-party dependency, `requests`.

``` bash
virtualenv -p python3 .
source bin/activate
pip install -r requirements.txt
```

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
usage: add_card [-h] --name NAME --board BOARD --column COLUMN
                [--comment COMMENT] [--label LABEL [LABEL ...]]
                [--config CONFIG] [--version]

add a card to a trello board

optional arguments:
  -h, --help            show this help message and exit
  --name NAME, -n NAME  name of the new card, please use double-quotes
  --board BOARD, -b BOARD
                        board the card should be added to, please use double-
                        quotes
  --column COLUMN, -o COLUMN
                        column the card should be added to, please use double-
                        quotes
  --comment COMMENT, -c COMMENT
                        comment to leave on the card, please use double-quotes
  --label LABEL [LABEL ...], -l LABEL [LABEL ...]
                        label to assign to the card, please use double-quotes
  --config CONFIG, -f CONFIG
                        config file, defaults to ./config.json
  --version, -v         show program's version number and exit

```

## Next Steps
- operation
    - debug mode with contextual logging, json-format
- packaging
    - either dockerfile or python package installable via pip
- testing
    - mocking the HTTP requests so functons can be unit-tested
- CI
    - automate both testing and packaging
- other features
    - colors for the labels?
    - take API key and Server Token as CLI args or env vars?

