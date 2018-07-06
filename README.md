# BitBucket Auto Merge

Use BitBucket's API to automatically create and merge pull requests. This is useful for including in your Pipelines steps to keep multiple branches insync with each other.

Take an example of where you're merging in hotfixes to the master branch throughout the day, instead of continuously merging the hotfixes branch back up to develop, you can just include this script to automatically make and merge pull requests up to develop.

This is based on the StackOverflow work done by svestka:
https://stackoverflow.com/a/47436375/1234292

Required arguments:
* `-s | --source`           Source git branch to create pull request from.
* `-d | --destination`      Destination git branch to merge pull request to.

Optional arguments:
* `-u | --user`             BitBucket username. If not set, uses BITBUCKET_AUTOMERGE_USER.
* `-p | --password`         BitBucket user password. If not set, uses BITBUCKET_AUTOMERGE_PASS.
* `--repo-owner`       The repository owner. If not set, uses BITBUCKET_REPO_OWNER.
* `--repo-slug`        The slug of the repository. If not set, uses BITBUCKET_REPO_SLUG.
* `--version`        Display the version of this script

Requirements:
*    `curl`  curl is a tool to transfer data from or to a server.
*    `jq`  jq is like sed for JSON data.

## Examples:
Create and automatically merge a pull request from master to develop:
```
# Merge master into develop
bitbucket-auto-merge -s master -d develop
```

All options:
```
bitbucket-auto-merge --source master --destination develop -u mfrank -p 4boo2 --repo-owner teamsystems --repo-slug hello-world
``` 

## License
MIT