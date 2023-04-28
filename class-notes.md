# Notes on github Actions
Book he is writing: https://www.amazon.com/Learning-GitHub-Actions-Automation-Integration/dp/109813107X

Actions -> workflow -> actions -> jobs

## What is is in the github Actions files
events (will triger) -> workflows -> job -> steps -> actions

* Jobs will run in parallel in different runners

### Events:
on: ...

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