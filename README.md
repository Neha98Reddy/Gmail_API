#Gmail API Email Processing
This project demonstrates how to integrate with the Gmail API using Python to fetch emails, process them based on specified rules, and take actions accordingly.

Getting Started
To get started with this project, follow these steps:

Prerequisites
Python 3.x installed on your machine.
Ensure you have a Google Cloud project set up with the Gmail API enabled.
Install necessary Python packages using pip:
bash
Copy code
pip install google-auth google-auth-oauthlib google-api-python-client
Setup
Clone the repository:

bash
Copy code
git clone <repository_url>
cd gmail-api-email-processing
Set up authentication credentials:

Download your OAuth client credentials (credentials.json) from Google Cloud Console and place it in the project directory.
Run the script to authenticate and fetch emails:

bash
Copy code
python main.py
Rules Configuration
Modify the rules.json file to define rules for processing emails based on specific conditions and actions. Example rules are provided in the file, which include conditions based on sender, subject, snippet, and date received.

Actions
Currently implemented actions include:

Printing email information (print_email_info).
Additional actions such as moving emails to the inbox or marking them as read can be added using the Gmail API. Refer to the Gmail API documentation for more information.
Rules Example
The rules.json file contains example rules for processing emails. Here are a couple of examples:

json
Copy code
[
    {
        "predicate": "All",
        "conditions": [
            {"field": "sender", "predicate": "equals", "value": "neha281432reddy@gmail.com"},
            {"field": "subject", "predicate": "contains", "value": "Acquisition"},
            {"field": "date_received", "predicate": "less than", "value": "2"}
        ],
        "actions": [
            {"action": "move_to_inbox"},
            {"action": "mark_as_read"},
            {"action": "print_email_info", "message": "Old email: {email_id} received on {date_received}"}
        ]
    },
    {
        "predicate": "Any",
        "conditions": [
            {"field": "snippet", "predicate": "contains", "value": "mail"},
            {"field": "date_received", "predicate": "less than", "value": "7"}
        ],
        "actions": [
            {"action": "print_email_info", "message": "Urgent or old email: {email_id} received on {date_received}"}
        ]
    }
]
Contributing
Feel free to contribute to this project by forking it and submitting pull requests. Any improvements or additional features are welcome!
