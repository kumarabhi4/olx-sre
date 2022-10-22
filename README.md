# This repository is for Udacity course on SRE with OLX sponsership


## Deployment Strategy 	
### Big-Bang:
    Replace A with B all at once.
### Blue Green:
    Two versions of production: Blue or previous version and Green or new version. Traffic can still be routed to blue while testing green. Switching to the new version is done by simply shifting traffic from blue to green.
### Canary:
    Aka Rolling Update, After deploying the new version, start routing traffic to new version little by little until all traffic is hitting the new production. Both versions coexist for a period of time.
### A/B Testing:
 	Similar to Canary, but instead of routing traffic to new version to accomplish a full deployment, you are testing your new version with a subset of users for feedback. You might end up routing all traffic to the new version, but that's always the goal.

## Build Stages

Think of stages like categories or types of jobs. Stages are used to group jobs and control timing.

### Build:
 	Everything that has to do with making code executable in production (e.g. Compile). The goal is to produce an artifact.
### Test:
 	All automated tests that verify at the code level.
### Analyze:
 	Any static analysis on the code or checking of dependencies.
### Deploy:
 	Anything to do with creating server instances or copying pre-built application files to an instance.
### Verify:
 	Any tests that can be run against a running instance of the application, often against a pre-production instance.
### Promote:
 	Replacing the current production environment with the new version which was just built and deployed.
### Revert:
 	Rolling back or undoing changes in case any verification fails after deployment.

## Single Responsibility Principle

    The single-responsibility principle (SRP) is a computer-programming principle that states that every module or class should have responsibility over a single part of the functionality provided by the software, and that responsibility should be entirely encapsulated by the class, module or function.


## Docker Images

## Image 		Use
	circleci/node 	For Node.JS server-side and networking applications.
	circleci/postgres 	For tasks that require PostgreSQL database functions.
	circleci/python 	For job that need to run Python or pip.
	alpine:latest 	A lightweight container for simple tasks.
	amazon/aws-cli 	For tasks that require the AWS CLI and related tools.

## Types of Steps

	Step Type 	Description
	checkout: 	Checks out the source code. Common to have this in all jobs in CI.
	run: 	Runs a shell command. Can name the step or simply execute a script.
	when: 	A conditional step that has its own steps that are run if the condition is true.
	save_cache and restore_cache: 	Save and restore files or folders. Cleaned up after pipeline finishes.
	persist_to_workspace and attach_workspace: 	Like a cache, but files are available for 15 days after pipeline.
	add_ssh_keys: 	Adding some additional ssh keys to the job for a tool that needs them (i.e. Ansible).
	store_artifacts: 	Makes an artifact, or file, available for download via CircleCI web app or API.
	store_test_results: 	Stores test results from test runner so that results are visible in Circle CI web app in the Test Summary section.
	"Orbs": 	Orbs, which we talked about already, are used like step types.