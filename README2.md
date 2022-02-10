MODILE 2
--------

Version Control with GIT
========================

### VERSION CONTROL:
    The practice of tracking and managing changes to software code

    # WHY:
        Version control systems allow you to compare files, identify differences, and merge the changes if needed prior to committing any code.
    
    # TYPES:
        1. Local Version Control --> Only Stored in Local Server
        2. Centralized Version Control --> Stored in Centralized Server
        3. Distributrd Version Control --> Stored in Centralized Server and Local Server
    
### GIT:
    Git is an Open-Source Distributed Version Control system (DVCS) which records changes made to the files laying emphasis on Speed, Data Integrity and Distributed, Non-linear workflows

    # CLONE:
        The creation of an organism that is an exact genitic copy of another 
        (Creting a Replica to the Remote repository Project)
    
    # PUSH:
        The Changes of the Local Repository move to the Remote repository
        (Move to our changes to the Remote Repository)

    # FETCH:
        Bring the latest repository to the Local repository
        (When using Fetch Both Old and New Versions are Available Local Repository)
    
    # PULL:
        PULL = FETCH + MERGE
        Bring the latest repository to the Local repository and Working Area also
        (Get the New Version Working Area and Local)

    Working Directory   Staging Area    Local Repo      Remote Repo

    | --Add-->        | --Commit-->         |  --Push-->    |
    
    | <-------------Checkout -------------- |               |

    |                 |                     |  <---Fetch ---|

    | <-------------Merge-------------------|               |

    | <--------------------------Pull---------------------- |

### GIT COMMANDS:
    # Add File to Staging Area
    **git add .**
        
    # Check Status
        **git status**
    # Commit the staged files to local Repository
        **git commit**

    # Diff between from Local and Working area Repository
        **git diff**

    # Show all the Commits
        **git log**

    # Create a Branch
        **git branch <branch_name>
    
    # Change the Branch
        **git checkout <branch name>

    # Channge the  last comit message using --amend option
        **git commmit --amend**
        
    # Remove from the staging area
        **git rm --cached <reponame/filename>
    
    # Add to Remote Repo
        **git remote add <Alias name (origin)> <git url>

    # Push the Data to repo master
        **git push <alias (origin)> <branch name (master)>**
    
    # Delete the Branch
        **git delete -d <Branch_name>
