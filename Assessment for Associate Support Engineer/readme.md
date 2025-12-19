# Assessment for Associate Support Engineer - Gitlab

## Matt Ellingsen
Hi - Thanks so much for choosing me to participate in the assessment!

## Assessment Questions:
#### 1. Write a Ruby or Bash script that will print usernames of all users on a Linux system together with their home directories.

   The simpliest resolution to this question is actually a command:
   > getent passwd | cut -d ':' -f 1,6
   
   Why does this work?
   The gentent command will get admin db entries and passwd command will steer us towards the user db.  These two commands will make up the basis of our search and the output will be a tablesque collection which includes the headers.

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

     
#### 2. We have sent you an image named `git_history.v3.png` showing a Git commit graph.
####   What sequence of Git commands could have produced the commit graph depicted in the image?

   Prior to the start of the image the code would have to be somehow moved to the "main" in the image.  While there are many scenarios to why you would be accessing code the most common would be with the following command:
   - git clone \<url\> - This would clone an existing repository onto your local machine.

   Once the code is local you can make any changes you'd like.  Once changes have been made you would 'add' any changes to a staging area using this command:
   - git add \<document\> - This will add the document to a list of staging files that have been added or altered.
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

   
#### 3. Write a brief blog post for GitLab that explains what Git is and what it can do for you.

   ### What is Git and How to Make it Work for You!!
   by Matt Ellingsen

   Have you ever wondered where the titles "Github" and "Gitlab" came from?  Did you just think it was a form of Git'er done?  Is Git a thing and how is it different from Gitlabs or Github?  If you've ever wondered any of these questions then sit back while I explain to you the answers to these questions plus many more!!
   
   #### What is Git?
   At its core Git is a versional control system for code and other documents.  It allows you track changes to code and other files over time while also being able revert back to previous versions if necessary.  Git is referred to as a distributed system because users are able to download the entire remote repository to their local system.  They can then work on their own local repository while other users also making changes on their own local repositories.  Users use a series of commands to create branches, commmits and merges on their local repository as well as re-updating their code with the remote "master" repository until ultimately pushes changes back to the master repository.

   #### What is Github and Gitlab?
   These are two platforms that both provide git as well as other supporting tools.  They are very similar in that they are both spaces to store code and other information for developers to work on code.  They both offer free and paid plans.  They differ in that Github focuses on more of collaborative environment for sharing projects.  GitLab is geared for more of a enterprise solution with more built in features for their customers.  


  - Q3 Tools and Sources:
    - https://about.gitlab.com/blog/
    - https://www.geeksforgeeks.org/git/what-is-git/
    - https://www.geeksforgeeks.org/git/introduction-to-github/
    - https://forum.gitlab.com/t/github-vs-gitlab-why-should-i-choose-gitlab/93945
    - https://www.bairesdev.com/blog/git-github-and-gitlab-whats-the-difference/



#### 4. Tell us about a recent issue you debugged or a problem you solved. How did you go about debugging it? What tools did you use? What was the outcome?

   The most recent project to have a major problem was while working on a project to use Elastic Beanstalk to upload a web application to AWS.  
   
   I had ChatGPT create for me the app I was going to use which is an application tracker app to keep track of job application and their statuses.  I had all of the folders structured correctly and zipped up appropriately but whenever I tried to run Elastic Beanstalk I would get an error message telling me that "Instance Deployment Failed".  Here are the steps I took to fix it.
   1.  ChatGPT told me to check the eb-engine log.  Looking at this log I Was able to determine Elastic Beanstalk couldn't read my Procfile correctly.
   2.  What's a Procfile?  I found out through google searches that a procfile is a file that defines the exact order, commands and tools to start an applications processes.
   3.  My Procfile was very simple.  It contained one line:  web: gunicorn app:application
   4.  Again I googled that line to figure out what it meant and found out that this is line is an attempt to create a webserver called Gunicorn.  The app:app at the end is referring to the name of the python file (app.py) and the second is the variable within the app.py file that refers to the flask object which in my case was this:  app = Flask(__name__)
   5.  Easy fix then, right?  I just change the Procfile to be web: gunicorn app:app and tried to run Elastic Beanstalk again. This time the Instance deployment was completed successfully but the health says degraded. When I click on view causes it says: Following services are not running: web.
   6.  At this point I wasn't sure where to turn.  The deployment had worked but the webserver Gunicorn had not started successfully.  I uploaded many of the files including the Procfile and app.py to ChatGPT and asked it to try to diagnose the issue.
   7.  The issue as it turns out was that the app = Flask(__name__) was within a function called create_app().
   8.  The solution was to add a line of code into app.py that was application = create_app() and then change the Procfile back to web: gunicorn app:application.  Now Elastic Beanstalk was able to create my job tracker app which I still use today.




#### Overall Tools and Sources:
- Markdown guide:
  - https://www.markdownguide.org/basic-syntax/
- Github:
  - https://github.com/MattE444/Portfolio-Projects-AWS/edit/main/Assessment%20for%20Associate%20Support%20Engineer/readme.md
    



