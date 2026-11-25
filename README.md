HR Assist – AI-Powered Employee Onboarding Assistant

Overview

Atliq HR Assist is an AI-powered HR assistant built using the Model Context Protocol (MCP). It automates common Human Resources tasks, particularly employee onboarding and HR operations.

The assistant enables an AI client to interact with HRMS functionality through MCP tools, allowing it to perform tasks such as adding employees, scheduling meetings, sending emails, creating IT requests, and managing employee leave.

Features

Employee Management – Add new employees and retrieve employee details.

Email Automation – Send welcome emails and notifications.

Ticket Management – Create, track, and update tickets for equipment and IT requirements.

Meeting Management – Schedule, retrieve, and cancel meetings.

Leave Management – Check leave balances, apply for leave, and retrieve leave history.

AI Tool Integration – Expose HR functionalities to an AI assistant through MCP tools.

Employee Onboarding Workflow – Assist with onboarding tasks through an AI-powered workflow.

Technology Stack

Python

Model Context Protocol (MCP)

FastMCP

Pydantic

SMTP / Email Automation

Python-dotenv

Architecture

The project follows a modular architecture, separating AI tool interfaces from business logic and data validation.

                  AI Client
              (Claude Desktop)
                     |
                     v
                MCP Server
                 server.py
                     |
       +-------------+--------------+
       |             |              |
       v             v              v
 Employee Tools  Leave Tools   Meeting Tools
       |             |              |
       +-------------+--------------+
                     |
                     v
             Manager Classes
          (Business Logic Layer)
                     |
                     v
              Data Management

              Email Automation
                     |
                     v
                 SMTP Server

Project Structure

Atliq-HR-Assist/
│
├── server.py
├── schemas.py
├── emails.py
├── hrms.py
├── utils.py
├── .env
├── requirements.txt
└── README.md

The project structure may vary depending on the implementation.

MCP Tools

The MCP server exposes the following tools to the AI client:

Tool

Description

add_employee

Add a new employee to the HRMS

get_employee_details

Retrieve employee details

send_email

Send emails to one or more recipients

create_ticket

Create equipment or IT-related tickets

update_ticket_status

Update the status of a ticket

list_tickets

Retrieve tickets for an employee

schedule_meeting

Schedule a meeting

get_meetings

Retrieve scheduled meetings

cancel_meeting

Cancel a meeting

get_employee_leave_balance

Check employee leave balance

apply_leave

Submit a leave application

get_leave_history

Retrieve leave history

MCP Prompt

The project also includes an onboarding prompt:

onboard_new_employee

This prompt guides the AI assistant through an employee onboarding workflow, including:

Adding the employee to the HRMS.

Sending a welcome email.

Notifying the employee's manager.

Creating equipment-related tickets.

Scheduling an introductory meeting.

Installation

1. Clone the repository

git clone <repository-url>
cd Atliq-HR-Assist

2. Create a virtual environment

python -m venv venv

Activate it:

Windows

venv\Scripts\activate

Linux / macOS

source venv/bin/activate

3. Install dependencies

pip install -r requirements.txt

Environment Variables

Create a .env file in the project directory.

CB_EMAIL=your_email@gmail.com
CB_EMAIL_PWD=your_email_app_password

These environment variables are used by the email functionality to authenticate with the SMTP server.

Security note: Never commit your .env file or expose your email credentials publicly.

Running the MCP Server

The MCP server uses the Standard Input/Output (stdio) transport.

Run the server using:

python server.py

The server initializes the HRMS managers, registers the MCP tools and prompts, and starts listening for requests from an MCP client.

MCP Client Configuration

The server can be configured in an MCP-compatible client such as Claude Desktop.

The client configuration should point to the Python executable and the project's server.py file.

Example configuration:

{
  "mcpServers": {
    "hr-assist": {
      "command": "python",
      "args": [
        "C:/path/to/Atliq-HR-Assist/server.py"
      ]
    }
  }
}

Replace the path with the actual location of your project.

Example Use Cases

Employee Onboarding

A user can request:

Onboard Rahul Sharma under manager EMP001.

The AI assistant can coordinate the onboarding process by:

Adding Rahul to the HRMS.

Sending a welcome email.

Notifying the manager.

Creating laptop and ID-card tickets.

Scheduling an introductory meeting.

Leave Management

Example requests:

What is Rahul's leave balance?

Apply leave for EMP001 for the requested dates.

Show the leave history of an employee.

IT Support

Example requests:

Create a laptop request for EMP001.

Create an ID-card ticket.

Show open tickets for an employee.

Update a ticket's status.

Key Concepts Demonstrated

This project demonstrates practical implementation of:

Model Context Protocol (MCP)

MCP tools and prompts

FastMCP server development

Python functions and decorators

Object-oriented programming

Classes, objects, and methods

Pydantic data validation and schemas

Modular software architecture

Environment variables and credential management

Email automation

AI-to-business-system integration

Disclaimer

This project is developed for learning and demonstration purposes. It uses simulated HRMS functionality and should be adapted with appropriate authentication, authorization, data security, logging, and database integration before being used in a production environment.
