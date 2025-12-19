# Assessment for Associate Support Engineer - Gitlab

## Matt Ellingsen
Hi - Thanks so much for choosing me to participate in the assessment!

## Assessment Questions:
1. Write a Ruby or Bash script that will print usernames of all users on a Linux system
   together with their home directories.

The simpliest resolution to this question is actually a command:  getent passwd | cut -d ':' -f 1,6
Why does this work?
The gentent command will fetch admin db entries and passwd command will steer us towards the user db.  These two commands will make up the basis of our search and the output will be a tablesque collection which includes the headers.

         1. Username
         2. Password
         3. User ID
         4. Group ID
         5. GECOS (comment field)
         6. Home Directory
         7. Login Shell

The cut command will filter the results of the above table, the -d is a delimiter which let us use the colon between the two fields and the -f 1,6 defines our two fields as #1 and #6 on the list above.
Finally, the pipe takes the output of the commands to the left of it and inputs it into the commands to its right.  

  - Tools and Sources:
    - https://www.reddit.com/r/linuxquestions/comments/mc061q/bash_script_for_printing_all_users_along_with/
    - Google Gemini prompt: breakdown this bash command for me and tell me what each part does getent passwd | cut -d ':' -f 1,6 

     
2. We have sent you an image named `git_history.v3.png` showing a Git commit graph.
   What sequence of Git commands could have produced the commit graph depicted in the image?
4. Write a brief blog post for GitLab that explains what Git is and what it can do for you.
5. Tell us about a recent issue you debugged or a problem you solved. How did you go about debugging it? What tools did you use? What was the outcome?


### Overall Tools and Sources:
- Markdown guide:
  - https://www.markdownguide.org/basic-syntax/
- Github:
  - https://github.com/MattE444/Portfolio-Projects-AWS/edit/main/Assessment%20for%20Associate%20Support%20Engineer/readme.md
    



