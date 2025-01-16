# Cursor Agent - Master Prompt

This prompt guides the agent through a task in a systematic way. It creates a clear record of every decision and milestone along the way, so you can always see what was done and why.

**Key Features:**

- **Automated Task Documentation**  
  Helps the agent set up and maintain a single “task file” that covers everything from the initial analysis all the way to final implementation.

- **Git Workflow Integration**  
  Gives the agent precise instructions on how to create branches, merge changes, and clean up repositories, ensuring a smooth and consistent version control process.

- **Checkpoint-Based Progress**  
  Sets up strategic pause points so the agent can confirm progress with you before moving forward, cutting down on wasted effort or heading off in the wrong direction.

- **Detailed Task Analysis**  
  Encourages thorough problem-solving before jumping into code changes, preventing rushed solutions and promoting a deeper understanding of the task.

- **Progress Tracking**  
  Keeps a chronological log of every attempt, success, and failure, making it easy to review what’s been tried and how it worked out.

- **Reusable Documentation**  
  Each task file can double as a standalone prompt for future collaboration on the task.

- **Source of Truth Management**  
  Centralizes all project decisions and progress notes in one place so there’s no confusion about what happened or why certain choices were made.

- **Final Review Process**  
  Walks the agent through a structured review to verify that every step is completed and documented properly before wrapping up the task.

## Get the prompt [HERE](https://raw.githubusercontent.com/maxfahl/cursor-agent-master-prompt/refs/heads/main/prompt.md). Copy/paste it into a the Cursor prompt box and change the below placeholders at the bottom to reflect your task and project overview etc.

```
[TASK]: <DESCRIBE YOUR TASK>
[PROJECT OVERVIEW]: <ENTER PROJECT OVERVIEW, OR LINK TO FILE CONTAINING THE DETAILS>
[MAIN BRANCH]: <YOUR MAIN BRANCH>
[YOLO MODE]: <ask|on|off>
```

For example:

```
[TASK]: Adding a todo item to the list via the form in `RELATIVE_PATH_TO_FILE` does notalways end up successfuly,
can you please help me figure out why it sometimes fails?

[PROJECT OVERVIEW]: PimpMyTask is a todo that... Here's a list of important files and what they do...

[MAIN BRANCH]: master (or any other feature branch you'd like to merge to when done)

[YOLO MODE]: off
```

- **Realtive paths instead of attachments:** I prefer linking to files and folders with their relative path instead of using the @-syntax, since it's easier to copy/paste the same prompt if needed. Sometimes Cursor doesn't parse the @-attachments as it should, and you will have to go in and edit them, which is a bit frustrating.
- **Project Overview:** I ususally iterate on this with the agent to build a `project_overview.md` placed in a `.notes` folder. I make it describe the most important files (or all files) thoroughly, as well as documenting a high level description of my project. When this is does you can point to it like `[PROJECT OVERVIEW]: .notes/project_overview.md (important information, please read)` or similar.
- **Yolo Mode:**
  - ask: The agent will ask you in the beginning if you want to enable "YOLO MODE" or not, you answer with `yes|no`.
  - on: The agent will perform all actions, and work through the steps, with minimal human intervention.
  - off: The agent will stop and ask you if it should procees at strategic places in the process.
  - note: I usually want to be kept in the loop, so I almost always set the YOLO mode to off.

> <br>
>
> **Caveats:**
> 1. Sometimes you will have to ask the agent to update the task file since it can easily forget this part of the process. When you do this, reference the task file at hand with the @ notation so that it doesn't create a new one.
> Here's the snippet I use when this happens:
> _```Now please update the "Task Progress" of our [TASK FILE]. Before updating it, please read the ENTIRE file so that you update yourself on our progress so far. If you feel the urge to create a new file, don't, instead look for the correct file in the `.tasks/` folder. The correct [TASK FILE] is the one matching the name of our current `git branch | cat`. Remember to keep the "Final Review" section at the bottom.```_
> **Power User Tip**: Install Raycast if you're on Mac, then create a snippet for this that auto expands when a specific keyword is entered. I use `!utf` for "Update Task File".
> 
> <br>

## Finalized Task File Example
Look at the [example-task-file-when-done.md](https://raw.githubusercontent.com/maxfahl/cursor-agent-master-prompt/refs/heads/main/example-task-file-when-done.md) file for an example of what the task file could look like when a task has been completed.

<br>
<br>

_**Now off you go! Feel free to fork or submit pull requests, I would love to collaborate.**_
