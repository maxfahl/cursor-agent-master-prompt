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

Get the prompt [HERE](https://raw.githubusercontent.com/maxfahl/cursor-agent-master-prompt/refs/heads/main/prompt.md). Copy/paste it into a the Cursor prompt box and change the below placeholders at the top to reflect your task and project overview etc.

```
[TASK]: <DESCRIBE YOUR TASK>
[PROJECT OVERVIEW]: <ENTER PROJECT OVERVIEW, OR LINK TO FILE CONTAINING THE DETAILS>
[MAIN BRANCH]: <YOUR MAIN BRANCH>
[YOLO MODE]: <ask|on|off>
```

Off you go! Feel free to fork or submit pull requests, I would love to collaborate.
