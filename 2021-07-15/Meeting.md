# Meeting of 15/07/2021

## Agenda

- Project:
  - Input file format
  - How is the data stored in the program memory
  - Project structure (folder heirachy)
    - test files
    - code files
  - Outline the process
    - Input
    - Processing
    - Output
  - [https://choosealicense.com/licenses/][Licensing]
- Git
  - How we will use Git
    - Pull Requests
    - Branches
  - How to setup git for commits to the repo.
    - in Project dir:
    1. Find your github noreply email
    2. add it to the local repository as follows
    git config user.email 'xxxxx+username@users.noreply.github.com'
    3. make commits as you did before
    - Resolving past commits with incorrect email. (just do
      it right the first time)
      - `git rebase -i HEAD~X -x 'git commit --amend --no-edit --author "Your Name <your@github.email>"'` X is the number of commits whihc have been made.
 - Commits
    - Commits should be made as frequently as possible. The changes should be small as possible to make it look good with `git log --graph --oneline`. Merging and rebasing also play a part here.
        - Creating a new file should be its own commit
        - Adding a function header should be its own commit
        - Modifications to a function should be an individual commit
        - We arent at the stage where we really have to worry about changes in multiple files for a single feature.
  - Merging and Rebasing
    - Rebase will be useful here but we will need to discuss it more in the meeting
    - See [github.com/mawww/kakoune][Kakoune] for a gross example of not merging enough

## Minutes

- Additional field to include for the input file:
  - Staff
    - Hours
    - Order of preferences?

- An array list of objects which will be used to store the information at the moment. This is so it can be returned.
   - Staff
      - Name: `String`
      - id: `String`
      - availability: `HashMap<String,ArrayList<int[2]>>`
      - preferences: `ArraList<Unit>`
   - Unit
    - Code: `String`,
    - numTutors: `Integer`,
    - schedule: `HashMap<String,ArrayList<int[2]>>`

- Folder structure will be under the MVC architecture.

- Software Development Lifecycle
  - Create Models (ignore the view at this point)
  - Controllers for logic
    - Define Controllers
      - File I/O Controllers
        - File Reading Controller
        - File Parser Controller
      - Data Processing Controllers. (does the allocation, blackbox for now)
  - Function headers - also declaration of data types
    - File I/O Controller
      - `ArrayList<String> readFile(String filename);`
    - File Parser Controller
      - `Timetable <ArrayList<Staff>,ArrayList<Unit>>  parseData(ArrayList<String>);`
    - Data Processing Controller
      - `Allocations generateAllocations(Timetable`

- An [https://github.com/Class-Scheduler][organisation] (*org*) will be used instead of the local repository. The devleopment process will be as follows:
  1. *Fork* the repository
  2. Clone your *fork* to *local*.
  3. **Make your changes**
  4. Merge from *org*/main to *fork*/main
  5. Merge/rebase your changes on top of the most recent files from *fork*
  6. Push from *local* to *fork*
  5. Pull request from *fork* to *org*.

