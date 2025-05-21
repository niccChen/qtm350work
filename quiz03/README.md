# QTM 350 - Data Science Computing

## Quiz 01 - Forking and Enhancing an Existing GitHub Repository

### Instructions

Please complete the following tasks using command-line operations and Git
commands as covered in Lectures 02 to 06. Paste all commands in a file named
`commands.txt`(or a Jupyter Notebook named `commands.ipynb`) located in the
repository's root directory. The final repository on GitHub should reflect all
changes made, and the `commands.txt` file should contain a list
of all commands used throughout the project.

Please send the link to your repository as a message on Canvas in the "Assignments" tab. There is a link for Quiz 01.

### Tasks

1. Fork this repository to your GitHub account.
2. Clone your forked repository to your local machine using the command line.
3. Change directory into the cloned repository.
4. Create a file named `commands.txt` (or `command.ipynb`) in the root of the repository to document all commands used throughout the project.
5. Create and switch to a new branch named `feature-update`.
6. Create a new directory called `reports` within the repository.
7. Inside the `reports` directory, create an empty file named `summary.md` using the command line.
8. Use a command to add the following line to `summary.md`: `This document provides a summary of the project updates.`
9. Add the newly created reports directory.
10. Commit the changes with the message "Add reports directory".
11. Create three empty text files named `file1.txt`, `file2.txt`, and `file3.txt` in the `reports` folder _using a single command with brace expansion_.
12. Rename the file `data/raw-data.csv` to `data/input-data.csv`.
13. Create a new directory named `backup` inside the `scripts` directory, then copy all `.py` files from the `scripts` directory to the newly created `backup` directory. _Use wildcards to copy the files and chain both commands in a single line of code_.
14. Delete the `docs/documentation.md` file.
15. Stage and commit all changes so far. Add the message "Update project files".
16. Create a new file named `.gitignore` in the root of the repository.
17. Add the following lines to `.gitignore` using the command line: 

```{markdown}
temp/
dataset0?.csv
```

18. Read the contents of your `.gitignore` file using the command line.
19. Stage and commit the `.gitignore` file with the message "Add .gitignore file". Use only one line to do both.
20. Switch back to the `main` branch and merge the `feature-update` branch into `main`.
21. Update the `commands.txt` file with all commands used so far, stage the file, commit it with a descriptive message, and push all changes to your forked GitHub repository
22. ...and you're done! 😊

## Bonus Questions

These bonus questions are designed to test advanced Git and GitHub skills. Attempt them only after completing the main assignment tasks and if you still have time (and like challenges). Document all steps and commands used.

1. Send a pull request with your changes to the original repository (this one). Document each step of the process.
2. Perform an interactive rebase to squash the last two commits into a single commit.
3. Implement a pre-commit hook that prevents commits if the `README.md` file is not updated. Provide the bash script for the hook and describe how to set it up. (This one is quite challenging.)

Best of luck!
