# Retry shell script

## Synopsis

    Retry a command several times
    Usage: retry [OPTION]... RETRY_COMMAND [SUCCESS_COMMAND]...
    
    -n, --number Number of retries (defaults to 30)
    -w, --wait   Seconds to wait before each retry (defaults to 2)
    -s, --silent Hide output of command
    -h, --help   Show this help
    
    Retries RETRY_COMMAND -n times and executes SUCCESS_COMMANDs
    after RETRY_COMMAND finally succeeded.

## Installation

    curl -sL "https://raw.githubusercontent.com/netresearch/retry/master/retry" -o /usr/local/bin/retry
    chmod +x /usr/local/bin/retry

## Example

    # Wait for a database connection to be available
    retry -s "mysql -e 'SELECT 1' -h $DATABASE_HOST -u $DATABASE_USER -p$DATABASE_PASSWORD $DATABASE_NAME" "echo 'Database ready'"
    
    # Is the same as
    retry -s "mysql -e 'SELECT 1' -h $DATABASE_HOST -u $DATABASE_USER -p$DATABASE_PASSWORD $DATABASE_NAME"
    echo "Database ready"
