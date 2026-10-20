
This is a repo for you, as an autonomous agent, to learn to do a specific project. You will build this repo of code for the project as you go. In the end you will have a working package of well-tested code along with documentation of the process by which you built the project.

## Conventions
- Agents write the README.md file as a reflection of the current state of the repo.
- Bilby writes the scope.md file as his understanding of the aims of project. At any time, scope.md may not be aligned with what is in the repo. It can be behind or ahead, you will need to infer this from the commit history or by asking Bilby. 
- scope.md is the most authoritative document describing the goals of the project.
- Don't use any local paths. Use environment variables and a git ignored `.env` instead. Any variables that must be set with `.env` should be described in the `README.md`.

### Forward planning
- The `spec/` folder holds detailed descriptions of the 
- `backlog.md` is a list of named, single-line descriptions of outstanding tasks that is linked to descriptions in the spec folder.
- Completed jobs from the backlog are removed from the backlog to `progress.md` where they are still described by a single line that also references relevant commits and (where possible) agent logs.

## Git
- We track text and code 
- We do not track model weights 
- We do not track input data
- We do not track output data

## Agent memory
- Each session is logged to a timestamped `.log` file in the `agent-logs` directory. The agent does this by appending learnings as it goes. 
- Every time an agent makes a commit, it carefully describes it in the log. 
- At the conclusion of a session, an agent always writes a 10-line summary of the session to the end of the log. A one-line summary is then added along with any relevant git commits to the `agent-logs/logs.json` json.

Agents can quickly understand previous sessions by checking the git history and cross-checking in `agent-logs/logs.json` or `agent-logs/*.log` for more detailed understanding of the reasoning.

## Rules
- You never make edits to scope.md
- Never schedule a job on an NCI login node that will take more than 30 minutes
- Computation is all done here on hectar. 
