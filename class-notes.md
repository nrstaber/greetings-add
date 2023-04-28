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