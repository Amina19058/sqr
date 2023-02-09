# Lab 1 -- Introduction to the quality gates


## Introduction

Welcome to the Software Quality and Reliability course. This course is  going to have 9 labs overall, and this one is going to be more of a warm-up then a lab. All of the labs have `Pass/Fail` grades, and will give you up to `30%` of overall grade. We would recommend to do all of them because labs are more or less simple, and will help you to work on your project. ***Let's roll!***

## Process of work with labs

- When doing a lab, you need to create a branch (or fork, which better) from `Lab` repository and work in your repo.
- To submit your lab you need to send `MR` from your branch/fork to the main repo. All discussion about lab is being conducted inside of your `MR`.
- Lab won't be checked if CI in your branch is failing , review your `MR` yourself before marking it. 
- If you need to create MR for some reason, but wont us to check it yet, please mark it as draft.

## Bug Bounty programm

If you've spotted some bugs or errors in code or description of the labs, you may create additional `MR` called `*your-surname*-lab-fixes`, you may get up to 10% overall improvement to your grade for the course based on your activity. Only the first one to spot a bug will receive a bug bounty, so check other bug-fixing MRs before submitting. **(It's not more then 10% for the whole course)**

## Quality gates

In any industry you need to have quality gates if you want to have more-or-less successfull ending to your project. One of the most popular tools in the modern software industry to automate work with quality gates is `CI/CD`. You check if your software satisfies quality gates on each step of CI/CD, by demanding appropriate results of builds/tests/lint, tools like GitLab/GitHub also providing possibilities to simplify work with code reviews and bug fixing.

In this lab we are going to develop simple CI/CD process using GitLab(which you almost definitely already know how to use), which we are going use as our basis for our next Labs, as you can see, this project already have some files inside of it, our lab today will be to make it build automatically.

## Lab

1. Create your branch of the `Lab1 - Introduction To the quality gates` repo. [***Here***](https://gitlab.com/sqr-inno/s23-lab-1-introduction-to-the-quality-gates)
2. Create `.gitlab-ci.yml` file inside of the repo
3. Add this code to your CI file and push it to your branch: 
```gitlab-ci.yml
stages:
  - build
  
build:
  stage: build
  image: maven
  script:
    - chmod +x mvnw
    - ./mvnw package
  artifacts:
    paths:
      - target/main-0.0.1-SNAPSHOT.jar
```
You should have working pipeline that automatically builds your project by now.

4. (optional) Let's add a bit of visuals, open `Readme.md` and then follow these steps:
- Go to Settings > CI / CD
- Expand the General pipelines settings section
- Scroll down to Pipeline status and/or Coverage report
- Select your branch
- Copy link for MD and paste it to the `Readme.md`
- You shoud see a lable `pipeline|{CI status}`


## Homework

As a homework you will need to add autodeploy to your project. I would recommend to use something like [AWS](https://console.aws.amazon.com), [Heroku](https://heroku.com) or [Digital Ocean](https://www.digitalocean.com/) (Digital Ocean and some other providers are free if you have [GitHub](https://education.github.com/students) license for students).  To check if server is running open this link: `http://<your-server>:8080/hello/`

**Lab is counted as done, if you have your app is running on server, and pipelines are passing.**

