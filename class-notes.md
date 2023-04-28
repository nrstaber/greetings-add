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
