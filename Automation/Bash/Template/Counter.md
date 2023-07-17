## Functions

The script contains a single function:

- `log()`: This function writes a log message to the log output file. It takes two arguments: the log type (can be "Error", "Warning", or "Info") and the log message. It then formats these into a JSON object and writes it to the log output file.

## Procedure

The script follows these steps:

1. It checks if the counter file exists. If it does not, the script creates it and initializes the counter to 0.
2. It reads the current counter value from the counter file.
3. It reads a specific field from the JSON log file to get the number it needs to count the occurrences of.
4. It counts the occurrences of this number in the JSON log file.
5. It adds this count to the current counter value.
6. It writes the new counter value to the counter file.
7. It logs the new counter value.

## Usage

The script does not take any command line arguments. To use the script, you need to:

1. Make sure the JSON log file, counter file, and log output file are correctly set in the script.
2. Set the field name you wish to search for in the jq commands.
3. Ensure you have jq and Python 3 installed on your machine.
4. Run the script in a Bash shell.

```bash
#!/bin/bash

# Define the JSON log file and the counter file
JSON_LOG_FILE_PATH="log.json"      # File where to search for the desired value
COUNTER_FILE_PATH="counter.txt"    # File to store the actual count
LOG_OUTPUT_FILE_PATH="log.txt"     # Script log output in json

log() {
    local log_type=$1
    shift
    local log_message=$@

    local status_code
    if [ "$log_type" == "Error" ]; then
        status_code=2
    elif [ "$log_type" == "Warning" ]; then
        status_code=1
    elif [ "$log_type" == "Info" ]; then
        status_code=0
    else
        echo "Invalid log type: $log_type"
        return
    fi

    local machine_hostname=$(hostname)

    formatted_log_message=$(python3 -c "import json, datetime; print(json.dumps({'timestamp': str(datetime.datetime.now()), 'type': '${log_type}', 'message': '${log_message}', 'status': ${status_code}, 'hostname': '${machine_hostname}'}))")

    echo "${formatted_log_message}" >> "${LOG_OUTPUT_FILE_PATH}"
}

# Check if the counter file exists and create it if it doesn't
if [ ! -f $COUNTER_FILE_PATH ]; then
    echo "0" > $COUNTER_FILE_PATH
fi

# Read the current counter value
current_counter_value=$(cat $COUNTER_FILE_PATH)

# Read the number to search for from a specific field of the JSON log file
search_number=$(jq -r '.field_name' $JSON_LOG_FILE_PATH)

# Count the occurrences of the number in the JSON log file
number_occurrences=$(jq -r '.[] | select(.field_name=='$search_number') | length' $JSON_LOG_FILE_PATH)

# Add the count to the counter
new_counter_value=$((current_counter_value + number_occurrences))

# Write the new counter value to the counter file
echo $new_counter_value > $COUNTER_FILE_PATH

# Log the new counter value
log "Info" "New counter value: $new_counter_value"
```

Version with counter for 1, 7, 30, 180, and 365d

```bash
#!/bin/bash

# Define the JSON log file and the counter file
JSON_LOG_FILE_PATH="log.json"      # File where to search for the desired value
COUNTER_FILE_PATH="counter.txt"    # File to store the actual count
LOG_OUTPUT_FILE_PATH="log.txt"     # Script log output in json

log() {
    local log_type=$1
    shift
    local log_message=$@

    local status_code
    if [ "$log_type" == "Error" ]; then
        status_code=2
    elif [ "$log_type" == "Warning" ]; then
        status_code=1
    elif [ "$log_type" == "Info" ]; then
        status_code=0
    else
        echo "Invalid log type: $log_type"
        return
    fi

    local machine_hostname=$(hostname)

    formatted_log_message=$(python3 -c "import json, datetime; print(json.dumps({'timestamp': str(datetime.datetime.now()), 'type': '${log_type}', 'message': '${log_message}', 'status': ${status_code}, 'hostname': '${machine_hostname}'}))")

    echo "${formatted_log_message}" >> "${LOG_OUTPUT_FILE_PATH}"
}

# Check if the counter file exists and create it if it doesn't
if [ ! -f $COUNTER_FILE_PATH ]; then
    echo "0" > $COUNTER_FILE_PATH
fi

# Read the current counter value
current_counter_value=$(cat $COUNTER_FILE_PATH)

# Read the number to search for from a specific field of the JSON log file
search_number=$(jq -r '.field_name' $JSON_LOG_FILE_PATH)

# Count the occurrences of the number in the JSON log file
number_occurrences=$(jq -r '.[] | select(.field_name=='$search_number') | length' $JSON_LOG_FILE_PATH)

# Add the count to the counter
new_counter_value=$((current_counter_value + number_occurrences))

# Write the new counter value to the counter file
echo $new_counter_value > $COUNTER_FILE_PATH

# Log the new counter value
log "Info" "New counter value: $new_counter_value"

# Get the current date
current_date=$(date +%s)

# Calculate the timestamps for 1 day, 7 days, 30 days, 180 days, and 1 year ago
timestamp_1_day_ago=$((current_date - 86400))  # 1 day = 86400 seconds
timestamp_7_days_ago=$((current_date - 604800))  # 7 days = 604800 seconds
timestamp_30_days_ago=$((current_date - 2592000))  # 30 days = 2592000 seconds
timestamp_180_days_ago=$((current_date - 15552000))  # 180 days = 15552000 seconds
timestamp_1_year_ago=$((current_date - 31536000))  # 1 year = 31536000 seconds

# Count the occurrences of the number in the specified time intervals
count_1_day=$(jq -r --arg timestamp "$timestamp_1_day_ago" '.[] | select(.field_name=='$search_number' and .timestamp >= $timestamp) | length' $JSON_LOG_FILE_PATH)
count_7_days=$(jq -r --arg timestamp "$timestamp_7_days_ago" '.[] | select(.field_name=='$search_number' and .timestamp >= $timestamp) | length' $JSON_LOG_FILE_PATH)
count_30_days=$(jq -r --arg timestamp "$timestamp_30_days_ago" '.[] | select(.field_name=='$search_number' and .timestamp >= $timestamp) | length' $JSON_LOG_FILE_PATH)
count_180_days=$(jq -r --arg timestamp "$timestamp_180_days_ago" '.[] | select(.field_name=='$search_number' and .timestamp >= $timestamp) | length' $JSON_LOG_FILE_PATH)
count_1_year=$(jq -r --arg timestamp "$timestamp_1_year_ago" '.[] | select(.field_name=='$search_number' and .timestamp >= $timestamp) | length' $JSON_LOG_FILE_PATH)

# Log the count numbers
log "Info" "Count for 1 day: $count_1_day"
log "Info" "Count for 7 days: $count_7_days"
log "Info" "Count for 30 days: $count_30_days"
log "Info" "Count for 180 days: $count_180_days"
log "Info" "Count for 1 year: $count_1_year"

```