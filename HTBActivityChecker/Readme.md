# Activity Tracker Script

## Overview
This script is designed to fetch and display activity data from Hack The Box (HTB) APIs for both teams and individual players. It supports dynamic column widths and includes additional details such as the `User ID` and `User Name` for activities performed by team members or players.

## Features
- Fetches and displays activity data for HTB teams or players.
- Dynamically adjusts column widths for better readability.
- Displays user-related data, including:
  - User ID
  - User Name
  - Activity Name
  - Date Difference
  - Activity Type
  - Date and Time of the activity.
- Refreshes API tokens when invalid or expired.

## Prerequisites
- A valid API token for accessing HTB APIs.
- `jq` installed for parsing JSON responses.
- `curl` installed for making HTTP requests.

## Setup
1. Save the script to a file, e.g., `activity_tracker.sh`.
2. Make the script executable:
```bash
chmod +x activity_tracker.sh
```
3. Ensure the `jq` tool is installed:
```bash
sudo apt-get install jq
```

## Usage
### Fetch Team Activity
```bash
./activity_tracker.sh -t <team_id>
```
Replace `<team_id>` with the ID of the team whose activity you want to fetch.

### Fetch Player Activity
```bash
./activity_tracker.sh -p <user_id>
```
Replace `<user_id>` with the ID of the player whose activity you want to fetch.

### Example Output
```plaintext
Name              User ID  User Name     Date Difference   Type       Date       Time
--------------------------------------------------------------------------------------
WayWitch          1671324  W40X          7 minutes ago     challenge  2024-11-22 15:29
BlockBlock        1443864  Danish4hmed   12 minutes ago    root       2024-11-22 15:25
BlockBlock        1443864  Danish4hmed   13 minutes ago    user       2024-11-22 15:23
Memento           1751812  0xos          52 minutes ago    challenge  2024-11-22 14:44
Vipère            1751812  0xos          52 minutes ago    challenge  2024-11-22 14:44
```

## Script Details

### Token Management
- On the first run, the script prompts you to enter an API token, which is saved to a `secret` file.
- If the token is invalid or expired, the script will prompt for a new token and update the `secret` file.

### Flags
- `-t`: Fetch team activity data.
- `-p`: Fetch player activity data.

### Dependencies
- `jq`: For parsing JSON responses.
- `curl`: For making HTTP requests.

## Error Handling
- If the API token is missing, expired, or invalid, the script will notify you and prompt for a new token.
- If no activity data is found for the given team or player, the script exits gracefully with a message.

## Example Commands
### Fetching Team Activity
```bash
./activity_tracker.sh -t 123
```

### Fetching Player Activity
```bash
./activity_tracker.sh -p 1111324
```

## Notes
- The script dynamically adjusts column widths to accommodate the longest entries.
- All sensitive data, such as the API token, is stored in the `secret` file and is only updated when necessary.
- The `Name`, `User ID`, and `User Name` fields are included to provide detailed insights into team activities.