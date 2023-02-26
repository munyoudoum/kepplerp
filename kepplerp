#!/bin/bash

# Check if node is installed
if ! command -v node &> /dev/null
then
    echo "node could not be found"
    exit
fi

# Check if ngrok is installed
if ! command -v ngrok &> /dev/null
then
    echo "ngrok could not be found"
    # install ngrok
    echo "Installing ngrok..."
    echo "npm install ngrok -g"
    npm install ngrok -g
    echo "ngrok installed"
fi

# Check if keppler is installed
if ! command -v keppler &> /dev/null
then
    echo "keppler could not be found"
    # install keppler
    echo "Installing keppler..."
    echo "npm install keppler -g"
    npm install keppler -g
    echo "keppler installed successfully"
fi

# Default values for optional arguments
DEBUG=1
NAME="folder name"
EXCLUDE="**/.DS_Store,**/node_modules/**,**/vendor/**,**/.git,**/.vscode,**/.env,**/.log,.idea/**,**/*___jb_old___,**/*___jb_tmp___"
OPEN=true
TEST=false
LIMIT=99
MAX_FILE_SIZE=99999
PORT=1571
NGROK_AUTH=""

# Parse command line arguments
while [[ $# -gt 0 ]]; do
    case "$1" in
        -d|--debug)
            DEBUG=$2
            shift
            shift
            ;;
        -n|--name)
            NAME=$2
            shift
            shift
            ;;
        -e|--exclude)
            EXCLUDE=$2
            shift
            shift
            ;;
        -o|--open)
            OPEN=$2
            shift
            shift
            ;;
        -t|--test)
            TEST=$2
            shift
            shift
            ;;
        -l|--limit)
            LIMIT=$2
            shift
            shift
            ;;
        -m|--max-file-size)
            MAX_FILE_SIZE=$2
            shift
            shift
            ;;
        -p|--port)
            PORT=$2
            shift
            shift
            ;;
        --auth)
            NGROK_AUTH=$2
            shift
            shift
            ;;
        *)
            # Unknown argument
            echo "Usage: $0 [-d DEBUG_LEVEL] [-n NAME] [-e EXCLUDE] [-o OPEN] [-t TEST] [-l LIMIT] [-m MAX_FILE_SIZE] [-p PORT] [--auth NGROK_AUTH]"
            exit 1
            ;;
    esac
done

# Run keppler with specified arguments
keppler "$NAME" --debug $DEBUG --port $PORT --exclude "$EXCLUDE" --open $OPEN --test $TEST --limit $LIMIT --max-file-size $MAX_FILE_SIZE >/dev/null 2>&1 &
echo "Keppler is running on port $PORT"

# Run ngrok to expose local server on the internet
if [ -n "$NGROK_AUTH" ]; then
  ngrok http $PORT --auth="$NGROK_AUTH"
  echo "ngrok is running with auth $NGROK_AUTH"
else
  ngrok http $PORT
  echo "ngrok is running without auth"
fi

wait
