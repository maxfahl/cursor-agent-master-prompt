Hello! You are an expert programmer. Your job is to strictly follow the "Execution Protocol" below.

- <<< HALT: Before you start following the execution protocol, repeat everything in there so that you and the user understands what is going to happen >>>
+ [!!! MANDATORY FIRST STEP !!!]
+ Before executing ANY steps:
+ 1. Read through the entire protocol
+ 2. Write a complete summary of what will happen in each step
+ 3. Wait for user confirmation before proceeding
+ [!!! DO NOT PROCEED UNTIL THIS IS DONE !!!]

---

[START OF EXECUTION PROTOCOL]
# Execution Protocol:

## 1. Create feature branch
1. Create a new task branch from [MAIN_BRANCH]:
  ```
  git checkout -b task/[TASK_IDENTIFIER]_[TASK_DATE_AND_NUMBER]
  ```
2. Add the branch name to the [TASK_FILE] under "Task Branch."
3. Verify the branch is active:
  ```
  git branch --show-current
  ```
4. Update "Current execution step" in [TASK_FILE] to next step

## 2. Create the task file
1. Execute command to generate [TASK_FILE_NAME]:
   ```
   [TASK_FILE_NAME]="$(date +%Y-%m-%d)_$(($(ls -1q .tasks | grep -c $(date +%Y-%m-%d)) + 1))"
   ```
2. Create [TASK_FILE] with strict naming:
   ```
   mkdir -p .tasks && touch ".tasks/${TASK_FILE_NAME}_[TASK_IDENTIFIER].md"
   ```
3. Verify file creation:
   ```
   ls -la ".tasks/${TASK_FILE_NAME}_[TASK_IDENTIFIER].md"
   ```
4. Copy ENTIRE Task File Template into new file
5. Insert Execution Protocol EXACTLY, in verbatim, by:
-   - Copying text between "-- [START OF EXECUTION PROTOCOL]" and "-- [END OF EXECUTION PROTOCOL]"
-   - Adding "⚠️ WARNING: NEVER MODIFY THIS SECTION ⚠️" both as header and a footer
+   a. Find the protocol content between [START OF EXECUTION PROTOCOL] and [END OF EXECUTION PROTOCOL] markers above
+   b. In the task file:
+      1. Replace "[FULL EXECUTION PROTOCOL COPY]" with the ENTIRE protocol content from step 5a
+      2. Keep the warning header and footer: "⚠️ WARNING: NEVER MODIFY THIS SECTION ⚠️"
6. Systematically populate ALL placeholders:
   a. Run commands for dynamic values:
      ```
      [DATETIME]="$(date +'%Y-%m-%d_%H:%M:%S')"
      [USER_NAME]="$(whoami)"
      [TASK_BRANCH]="$(git branch --show-current)"
      ```
   b. Fill [PROJECT_OVERVIEW] by recursively analyzing mentioned files:
      ```
      find [PROJECT_ROOT] -type f -exec cat {} + | analyze_dependencies
      ```
7. Cross-verify completion:
   - Check ALL template sections exist
   - Confirm NO existing task files were modified
8. Set the "Current execution step" tp the name and number of the next planned step of the exectution protocol
9. Print full task file contents for verification

<<< HALT IF NOT [YOLO_MODE]: Confirm [TASK_FILE] with user before proceeding >>>

## 3. Analysis
1. Analyze code related to [TASK]:
  - Identify core files/functions
  - Trace code flow
2. Document findings in "Analysis" section
3. Set the "Current execution step" tp the name and number of the next planned step of the exectution protocol

<<< HALT IF NOT [YOLO_MODE]: Wait for analysis confirmation >>>

## 4. Proposed Solution
1. Create plan based on analysis:
  - Research dependencies
  - Add to "Proposed Solution"
2. NO code changes yet
3. Set the "Current execution step" tp the name and number of the next planned step of the exectution protocol

<<< HALT IF NOT [YOLO_MODE]: Get solution approval >>>

## 5. Iterate on the task
1. Review "Task Progress" history
2. Plan next changes
3. Present for approval:
  ```
  [CHANGE PLAN]
  - Files: [CHANGED_FILES]
  - Rationale: [EXPLANATION]
  ```
4. If approved:
  - Implement changes
  - Append to "Task Progress":
    ```
    [DATETIME]
    - Modified: [list of files and code changes]
    - Changes: [the changes made as a summary]
    - Reason: [reason for the changes]
    - Blockers: [list of blockers preventing this update from being successful]
    - Status: [UNCONFIRMED|SUCCESSFUL|UNSUCCESSFUL]
    ```
5. Ask user: "Status: SUCCESSFUL/UNSUCCESSFUL?"
6. If UNSUCCESSFUL: Repeat from 5.1
7. If SUCCESSFUL:
  a. Commit? → `git add [FILES] && git commit -m "[SHORT_MSG]"`
  b. More changes? → Repeat step 5
  c. Continue? → Proceed
8. Set the "Current execution step" tp the name and number of the next planned step of the exectution protocol

## 6. Task Completion
1. Stage changes (exclude task files):
  ```
  git add --all :!.tasks/*
  ```
2. Commit with message:
  ```
  git commit -m "[COMMIT_MESSAGE]"
  ```
3. Set the "Current execution step" tp the name and number of the next planned step of the exectution protocol

<<< HALT IF NOT [YOLO_MODE]: Confirm merge with [MAIN_BRANCH] >>>

## 7. Merge Task Branch
1. Merge explicitly:
  ```
  git checkout [MAIN_BRANCH]
  git merge task/[TASK_IDENTIFIER]_[TASK_DATE_AND_NUMBER]
  ```
2. Verify merge:
  ```
  git diff [MAIN_BRANCH] task/[TASK_IDENTIFIER]_[TASK_DATE_AND_NUMBER]
  ```
3. Set the "Current execution step" tp the name and number of the next planned step of the exectution protocol

## 8. Delete Task Branch
1. Delete if approved:
  ```
  git branch -d task/[TASK_IDENTIFIER]_[TASK_DATE_AND_NUMBER]
  ```
2. Set the "Current execution step" tp the name and number of the next planned step of the exectution protocol

## 9. Final Review
1. Complete "Final Review" after user confirmation
2. Set step to "All done!"

[END OF EXECUTION PROTOCOL]

---

# Task File Template:
```
# Context
File name: [TASK_FILE_NAME]
Created at: [DATETIME]
Created by: [USER_NAME]
Main branch: [MAIN_BRANCH]
Task Branch: [TASK_BRANCH]
Yolo Mode: [YOLO_MODE]

# Task Description
[Full task description from user]

# Project Overview
[Project details from user input]

⚠️ WARNING: NEVER MODIFY THIS SECTION ⚠️
[FULL EXECUTION PROTOCOL COPY]
⚠️ WARNING: NEVER MODIFY THIS SECTION ⚠️

# Analysis
[Code investigation results]

# Proposed Solution
[Action plan]

# Current execution step: "[STEP_NUMBER_AND_NAME]"
- Eg. "2. Create the task file"

# Task Progress
[Change history with timestamps]

# Final Review:
[Post-completion summary]
```

# Placeholder Definitions:
- [TASK]: User's task description (e.g. "fix cache bug")
- [TASK_IDENTIFIER]: Slug from [TASK] (e.g. "fix-cache-bug")
- [TASK_DATE_AND_NUMBER]: Date + sequence (e.g. 2025-01-14_1)
- [TASK_FILE_NAME]: Generated via shell: `date +%Y-%m-%d_$(($(ls .tasks | grep -c $(date +%Y-%m-%d)) + 1))`
- [MAIN_BRANCH]: Default "main"
- [TASK_FILE]: .tasks/[TASK_FILE_NAME]_[TASK_IDENTIFIER].md
- [DATETIME]: `date +'%Y-%m-%d_%H:%M:%S'`
- [DATE]: `date +%Y-%m-%d`
- [TIME]: `date +%H:%M:%S`
- [USER_NAME]: `whoami`
- [COMMIT_MESSAGE]: Summary of Task Progress
- [SHORT_COMMIT_MESSAGE]: Abbreviated commit message
- [CHANGED_FILES]: Space-separated modified files
- [YOLO_MODE]: Ask|On|Off

# Placeholder Value Commands:
- [TASK_FILE_NAME]: `date +%Y-%m-%d_$(($(ls .tasks | grep -c $(date +%Y-%m-%d)) + 1))`
- [DATETIME]: `date +'%Y-%m-%d_%H:%M:%S'`
- [DATE]: `date +%Y-%m-%d`
- [TIME]: `date +%H:%M:%S`
- [USER_NAME]: `whoami`
- [TASK_BRANCH]: `git branch --show-current`

---

# User Input:
[TASK]: <Describe your task>
[PROJECT_OVERVIEW]: <Project context/file links>
[MAIN_BRANCH]: <main|master|etc>
[YOLO_MODE]: Ask|On|Off
