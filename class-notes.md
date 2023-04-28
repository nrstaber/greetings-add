# Notes on github Actions
Book he is writing: https://www.amazon.com/Learning-GitHub-Actions-Automation-Integration/dp/109813107X

Actions -> workflow -> actions -> jobs

## What is is in the github Actions files
events (will triger) -> workflows -> job -> steps -> actions

* Jobs will run in parallel in different runners

### Events:
on: ...
#### Workflow_dispatch
* you can add manually start a workflow by using `workflow_dispatch`
* This is helpful if your trying to debug something with the workflow
* This has to be on the main branch
* you can accessed by using `github.event.inputs.<name>`
workflow_dispatch:
    inputs:
        myValues:
            description: 'Input Values'

### Jobs
jobs:
    build:
        steps:
        - uses: actions/checkout@v2 (This v2 can be branch or other things)

## github Actions storage - Artifacts
* you can create a artifact that can be used in another job.
* They are storage for 90 days.
uses: actions/upload-artifact@v2
with:
    name: theNameGoesHere
    path: build/libs

## Finding different actions
https://github.com/marketplace?type=actions

## Environment files
* you can make variables that can be used after.
* command is `run:` then using it after `${{ <type>.<name> }}` (Example has env but I have been using secrets)

## How do output from a step in another step
* Need `id:`
* format for reference `${{steps.<step id>.outputs.<name of output parameter>}}`
outputs:
    artifact-tag: ${{ steps.changelog.outputs.version }}
* to tell the job that needs to wait for another job add `needs: <job name>` then add to a step what you need 
    `${{needs.<name of job>.outputs.<job output name> }}`

## Accessing a file within the repostiory
* you can store the files the artifact then you can use them in another job.

## Testing with Github Actions

## Custom Actions
* `uses: <repo name>/<action name>@<tag>`

## Logs
* To share the log you can right click and copy the link for that line. Look for `Copy Clean Link`
* you can add warnings, debug, and errors into your github Actions
    * by adding `run: echo "::warning::Text goes here"`

## Secrets
* It will not be print out the secrets when logging. It will print as ****
* GITHUB_TOKEN might be more save than secrets. `gitub.token`

## Script Injection
* you will need to clean your inputs.
* Your title of pull request could create problems too.

## Other items
* On `run: |` then the next lines you can run and can have more than one line.
    * it is really the `|` that does it.
* `.` let your use VSCode in github
* After create a badge from the Action tab you can copy the it and add it to md file.
Here is the badge: 
[![Simple Pipe](https://github.com/nrstaber/greetings-add/actions/workflows/pipeline.yml/badge.svg)](https://github.com/nrstaber/greetings-add/actions/workflows/pipeline.yml)
