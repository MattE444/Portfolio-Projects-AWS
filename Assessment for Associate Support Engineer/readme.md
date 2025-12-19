# Assessment for Associate Support Engineer - Gitlab

## Matt Ellingsen
Hi - Thanks so much for choosing me to participate in the assessment!

## Assessment Questions:
1. Write a Ruby or Bash script that will print usernames of all users on a Linux system
   together with their home directories.

   The simpliest resolution to this question is actually a command:
   > getent passwd | cut -d ':' -f 1,6
   
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


  - Q1 Tools and Sources:
    - https://www.reddit.com/r/linuxquestions/comments/mc061q/bash_script_for_printing_all_users_along_with/
    - Google Gemini:
      - prompt: breakdown this bash command for me and tell me what each part does getent passwd | cut -d ':' -f 1,6
      - prompt: what are all of the fields that getent passwd includes?

     
2. We have sent you an image named `git_history.v3.png` showing a Git commit graph.
   What sequence of Git commands could have produced the commit graph depicted in the image?

   Prior to the start of the image the code would have to be somehow moved to the "main" in the image.  While there are many scenarios to why you would be accessing code the most common would be with the following command:
   - git clone <url> - This would clone an existing repository onto your local machine.

   Once the code is local you can make any changes you'd like.  Once changes have been made you would 'add' any changes to a staging area using this command:
   - git add <document> - This will add the document to a list of staging files that have been added or altered.
   - git status - This will show all documents that have currently been added to the staging area as well as those that have been altered but not yet added to staging.
  
   Now we come to the left side of the image.  The first two white circles are the first two commits.  They would be done with following commands:
   - git commit -m "comments about the first commit" - This would save a snapshot of the project including any 'add's or changes made since the last commit.  Comments about what was changed can also be included.
   - git commit -m "comments about the second commit" - Another snapshot taken and saved with any changes made since the first commit happened.

   At this point in the image something new happens.  While there is a third commin happening in the main branch.  We also have a new awesome feature being developed in tandem.  This new awesome feature has been broken out from the main branch with the following command:
   - git checkout -b feature-branch - This will create a new branch of code named "feature-branch" and will be separate from the main branch.
   - git commit -m "comments about the third commit" - Meanwhile, the main branch is still seeing commits with new changes being incorporated into the main branch but exluding the work being done in the feature branch.
  
   Now we come to the fourth white circle in the main line of circles. This one is entitled "Merge".  It is here that we've completed our work in the feature branch and are going to incorporate it back into the main branch.  We do it with this command:
   - git merge feature-branch - This will merge all of the code changes from the feature branch into the main branch.

   Finally, we come to the last greenish circle.  This is our latest commit and brings us up to current time.  The last commit is just like the others:
   - git commit -m "comments about the fourth commit" - This commit will include all of the changes made since the third commit including those made from the recently merged feature branch.

   
  - Q2 Tools and Sources:
    - https://www.theodinproject.com/lessons/foundations-git-basics
    - Google Gemini:
      - prompt: Explain this image to me as it applies to git
      - prompt: Explain the specific Git commands you would use to recreate this exact history.

   
3. Write a brief blog post for GitLab that explains what Git is and what it can do for you.

   






  - Q3 Tools and Sources:
    - https://www.theodinproject.com/lessons/foundations-git-basics
    - Google Gemini:
      - prompt: Explain this image to me as it applies to git
      - prompt: Explain the specific Git commands you would use to recreate this exact history.



5. Tell us about a recent issue you debugged or a problem you solved. How did you go about debugging it? What tools did you use? What was the outcome?


### Overall Tools and Sources:
- Markdown guide:
  - https://www.markdownguide.org/basic-syntax/
- Github:
  - https://github.com/MattE444/Portfolio-Projects-AWS/edit/main/Assessment%20for%20Associate%20Support%20Engineer/readme.md
    



