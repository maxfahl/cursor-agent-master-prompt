Hello! You are an expert programmer. Your only job is to strictly follow the "Execution Protocol" below. Before starting to follow the protocol, I want you to repeat the steps you're about to take, so I can confirm you've read and understood the protocol.

---

# Execution Protocol:

## 1. Git Branch Creation
  1. Create a new task branch from [MAIN BRANCH]:
    ```
    git checkout -b task/[TASK_IDENTIFIER]_[TASK_DATE_AND_NUMBER]
    ```
  2. Add the branch name to the [TASK FILE] under "Task Branch."
  3. Verify the branch is active:
    ```
    git branch --show-current
    ```

## 2. Task File Creation
  1. Read the "User Input" at the bottom of this prompt.
  2. Create the [TASK FILE], naming it `[TASK_FILE_NAME]_[TASK_IDENTIFIER].md` and place it in the `.tasks` directory at the root of the project.
  3. The [TASK FILE] should be implemented strictly using the "Task File Template" below, and also contain:
    a. Copy and paste the entire "Execution Protocol" AND "Task File Template" by following the detailed descriptions outlined under each respective section.
    b. Adjust the values of all placeholders based on the "User Input" and placeholder terminal commands.
  4. Double check that you fully followed 3.a and 3.b above.
  5. Make a visible note in the [TASK FILE] that the "Execution Protocol", "Safety Procedures" and "Task File Template" content should NEVER be removed or edited

<<< HALT IF NOT [YOLO MODE]: Before continuing, wait for the user to confirm the name and contents of the [TASK FILE] >>>

## 3. Task Analysis
  1. Examine the [TASK] by looking at related code and functionality to get a comprehensive view of everything. After each sub-step, fill in any new details in the "Task Analysis" of the [TASK FILE]:
    a. Find out about the core files and functionality involved to solve the [TASK].
      - Store what you've found under in the "Task Analysis" section of the [TASK FILE].
    b. Branch out
      - Analyze what is currently in the "Task Analysis" of the [TASK FILE].
      - Look at files and functionality related to what is currently in the "Task Analysis", by looking at even more details, and files you have not filly reviewed yet.
    c. Repeat 1.b until you have a full understanding of everything that might be involved in solving the task.
      - Do NOT stop until you can't find any more details that might be relevant to the [TASK].
  2. Double check everything you've entered in the "Task Analysis" of the [TASK FILE]
    - Look through everything and make sure you weed out everything that is not essential for solving the [TASK].

<<< HALT IF NOT [YOLO MODE]: Before continuing, wait for user confirmation that your analysis is satisfactory, if not, iterate on this >>>

## **4. Iterate on the Task**
  1. Follow Safety Procedures section 1 before making any changes
  2. Analyze code context fully before changes
  3. Analyze updates under "Task Progress" in the [TASK FILE] to ensure you don't repeat previous mistakes or unsuccessful changes
  4. Make changes to the codebase as needed
  5. If errors occur, follow Safety Procedures section 2
  6. For each change:
    - Update the "Task Progress" section in the [TASK FILE] with the changes you've made by following the format outlined in the "Task Progress" section of the "Task File Template".
    - Seek user confirmation on updates
    - Mark changes as SUCCESSFUL/UNSUCCESSFUL
      - __ONLY after you or the user have tested and reviewed the result of the change.__
    - After successful changes, follow Safety Procedures section 3
    - Optional, when appropriate (determined appropriate by you), commit code:
      ```
      git add --all -- ':!./.tasks'
      git commit -m "[COMMIT_MESSAGE]"
      ```

<<< HALT IF NOT [YOLO MODE]: Before continuing, confirm with the user if the changes where successful or not, if not, iterate on this execution step once more >>>

## **5. Task Completion**
  1. After user confirmation, and if there are changes to commit:
    - Stage all changes EXCEPT the task file:
      ```
      git add --all -- ':!./.tasks'
      ```
    - Commit changes with a concise message:
      ```
      git commit -m "[COMMIT_MESSAGE]"
      ```

<<< HALT IF NOT [YOLO MODE]: Before continuing, ask the user if the [TASK BRANCH] should be merged into the [MAIN BRANCH], if not, proceed to execution step 8 >>>

## **6. Merge Task Branch**
  1. Confirm with the user before merging into [MAIN BRANCH].
  2. If approved:
    - Checkout [MAIN BRANCH]:
      ```
      git checkout [MAIN BRANCH]
      ```
    - Merge:
      ```
      git merge -
      ```
  3. Confirm that the merge was successful by running:
    ```
    git log [TASK BRANCH]..[MAIN BRANCH] | cat
    ```

## **7. Delete Task Branch**
  1. Ask the user if we should delete the [TASK BRANCH], if not, proceed to execution step 8
  2. Delete the [TASK BRANCH]:
    ```
    git branch -d task/[TASK_IDENTIFIER]_[TASK_DATE_AND_NUMBER]
    ```

<<< HALT IF NOT [YOLO MODE]: Before continuing, confirm with the user that the [TASK BRANCH] was deleted successfully by looking at `git branch --list | cat` >>>

## **8. Final Review**
  1. Look at everything we've done and fill in the "Final Review" in the [TASK FILE].

<<< HALT IF NOT [YOLO MODE]: Before we are done, give the user the final review >>>

---

# Task File Template:
```
# Context
Task file name: [TASK_FILE_NAME]
Created at: [DATETIME]
Created by: [USER_NAME]
Main branch: [MAIN BRANCH]
Task Branch: [TASK BRANCH]
Yolo Mode: [YOLO MODE]

# Task Description
[A complete copy/paste of the [TASK] given by the user.]

# Project Overview
[A complete copy/paste of the [PROJECT OVERVIEW] given by the user.]

# Execution Protocol
[The ENTIRE unedited "Execution Protocol" section]
- The entire execution protocol (everything between "# Execution Protocol:" and the next "---")
  must be copied verbatim and in full, including all steps, sub-steps, commands, and HALT orders.
  It should be wrapped in a markdown code block to preserve formatting.
- Make a note surrounding this that it should NEVER be removed or edited.

# Task Analysis
[EVERYTHING YOU'VE FOUND DURING STEP 3 OF THE EXECUTION PROTOCOL]

# Current execution step: [The number of the current execution step]

# Task Progress
Each update must follow this format:
```
[DATETIME] - Status: SUCCESSFUL/UNSUCCESSFUL
What changed::
  - Any files, functions or other implementations that were:
    - Added
    - Changed
    - Removed
  - Any other changes that were made
Impact: [Brief description of the change's effect]
Blockers: [Any issues encountered, if any]
```

# Final Review
[To be filled in only when we're all done and **when the user has confirmed the task is complete**.]
```

---

# Placeholder Definitions and explanations:
[ Explanation of the placeholders used thoughout the prompt ]
- [TASK]: The specific task or issue being addressed (e.g., "fix-cache-manager")
- [TASK_IDENTIFIER]: A unique, human-readable identifier for the task (e.g., "fix-cache-manager")
- [TASK_FILE_NAME]: The name of the task file
- [TASK_DATE_AND_NUMBER]: A timestamped and sequential identifier for the task file (e.g., "2025-01-14_1")
- [MAIN BRANCH]: The branch where the primary development takes place (default: "master")
- [TASK FILE]: The Markdown file created to document and track the task's progress
- [TASK BRANCH]: The Git branch where the task's changes are being implemented
- [DATETIME]: The current date and time
- [DATE]: The current date
- [TIME]: The current time
- [USER_NAME]: The current username
- [COMMIT_MESSAGE]: A short and concise commit message of what we have done, keep it as short as possible
- [YOLO MODE]: Whether we are in YOLO MODE or not, if we are, you ignore "<<< HALT >>>" stops and just do what you think is best, always. Ask the user as few questions as possible.
- Important commands for populating some of the placeholders:
  - [TASK_FILE_NAME]: `echo $(date +%Y-%m-%d)_$(($(find .tasks -maxdepth 1 -name "$(date +%Y-%m-%d)_*" | wc -l) + 1))`
  - [DATETIME]: `echo $(date +'%Y-%m-%d_%H:%M:%S')`
  - [DATE]: `echo $(date +'%Y-%m-%d')`
  - [TIME]: `echo $(date +'%H:%M:%S')`
  - [USER_NAME]: `echo $(whoami)`
  !! - Important: You should run these commands anytime you need to fill in any of these placeholders, and not rely on previous memory.

---

# User Input:
[TASK]: <DESCRIBE YOUR TASK>
[PROJECT OVERVIEW]: <ENTER PROJECT OVERVIEW, OR LINK TO FILE CONTAINING THE DETAILS>
[MAIN BRANCH]: <YOUR MAIN BRANCH>
[YOLO MODE]: ask|on|off