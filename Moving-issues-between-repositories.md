Currently GitHub does not support moving issues between repositories. We can get around this limitation by using api to copy issues and comments one by one (but information about op won't be retained).

There's a bug with most implementation that GitHub will answer with 403 code after importing 35 comments, which crashes importer.

Here are steps to get around this bug and import larger threads:

- Install npm ([link for Windows installer](https://nodejs.org/en/download/))
- Create [personal access token](https://help.github.com/articles/creating-a-personal-access-token-for-the-command-line/)
- `git clone https://github.com/buildo/gh-issue-mover.git`
- `cd gh-issue-mover`
- **`git checkout fix-rate-limiting`** - on this branch the bug mentioned earlier is fixed
- `npm install -g`
- Modify `config.json.example`:
    - Change owner and name of source and destination repository (sinara-hw is the owner in our case)
    - Insert token generated in previous steps
    - Remove `rootURL` line
    - Remove commas before closing bracket `}` (line 5 and 10)
- Run `gh-issue-mover --config config.json.example`
    - Follow instructions (insert issue number without # sign)

For results see [imported issue](https://github.com/sinara-hw/Kasli/issues/5) and [original](https://github.com/sinara-hw/sinara/issues/499).