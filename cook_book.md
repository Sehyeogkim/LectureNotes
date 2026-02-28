# Git Parallel Cookbook for Multi-Agent Work

## Short Answer to Your Main Questions

1. Yes, people run multiple terminals and multiple AI agents in parallel.
2. For local development, the common safe pattern is:
   - one branch per task
   - one worktree (separate directory) per active branch/agent
3. Two agents should not actively edit the same directory at the same time.
4. You can switch branches in one directory, but that is a sequential workflow, not true parallel work.
5. Yes, after parallel work on separate branches, you merge the branches.

## Important Git Commands for Parallel Agent Work

### Branch basics
```bash
git branch                   # list local branches
git switch main              # switch branch
git switch -c feature/auth   # create + switch to a new branch
git merge feature/auth       # merge branch into current branch
git rebase main              # rebase current branch on main
```

### Worktree basics (key for parallel agents)
```bash
git worktree list
git worktree add ../wt-auth -b feature/auth main
git worktree add ../wt-fix bugfix/login
git worktree remove ../wt-auth
git worktree prune
```

### Helpful safety/inspection commands
```bash
git status
git log --oneline --graph --decorate --all -n 30
git diff
git branch -vv
```

## Your Scenarios (A/B branch, dir1/dir2)

### Scenario 1: `branch A - dir1`, `branch B - dir1` (single directory)
- This means switching branches back and forth in one folder.
- Good for one person doing one task at a time.
- Bad for parallel agents because:
  - uncommitted changes collide
  - stashing/context switching overhead
  - high chance of mistakes

### Scenario 2: `branch A - dir1`, `branch B - dir2` (separate directories/worktrees)
- This is the recommended parallel setup.
- Each agent gets isolated files and branch context.
- You can run tests/builds simultaneously for different tasks.
- Easier review and cleaner diffs.

## What Is More Efficient, and When?

### Use single directory + branch switching when:
- only one active task
- very short edits
- no need for parallel execution

### Use multiple worktrees when:
- multiple agents/humans work concurrently
- features are independent
- you need long-running tasks in parallel (tests, refactors, bugfixes)
- you want low context-switch cost and safer isolation

## Practical Pattern for 2 Agents

```bash
# from main repo dir (dir1)
git switch main
git pull

# create worktree for agent1
git worktree add ../dir_agent1 -b feature/A main

# create worktree for agent2
git worktree add ../dir_agent2 -b feature/B main
```

Then:
- Agent1 works only in `../dir_agent1`
- Agent2 works only in `../dir_agent2`
- Commit separately
- Open PRs or merge branches after review

## Reality Check: How People Use It

In real workflows, teams increasingly use worktrees for parallel AI/human coding because branch switching in one folder does not scale well with multiple active tasks. This is especially true when two agents run at once.

## Notes for Current Claude/Codex-style Agent Workflows

- Local multi-agent sessions: worktree-per-agent is the safest default.
- Cloud agent systems may run each task in isolated sandboxes (different from your local filesystem), but local Git integration still benefits from branch/worktree discipline.

## Sources

- Git official docs: `git worktree`  
  https://git-scm.com/docs/git-worktree
- Git official docs: `git branch`  
  https://git-scm.com/docs/git-branch
- OpenAI Codex announcement (parallel task context in isolated environments)  
  https://openai.com/index/introducing-codex/
