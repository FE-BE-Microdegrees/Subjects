# Github Issue

In this topic we'll explore the Github Issue feature - what it is, how to use it, and why it's useful.

![Issue](Issue.webp)

Image source: Dall-E by OpenAI

- [Github Issue](#github-issue)
  - [Learning Outcomes](#learning-outcomes)
  - [What is a _Github Issue_?](#what-is-a-github-issue)
  - [Why Use _Github Issues_?](#why-use-github-issues)
  - [Best Practices for Writing _Issues_](#best-practices-for-writing-issues)
  - [Example of a Well-Structured _Issue_](#example-of-a-well-structured-issue)
  - [Example of a Poorly Written _Issue_](#example-of-a-poorly-written-issue)
  - [Exercises](#exercises)

All projects need a system to help organize the workflow and keep an eye on it. There are many different tools for this, **GitHub Issues** is just one of the many available in the market.

## Learning Outcomes

After completing this chapter, you will be able to:

- Describe what a _Github Issue_ is and how to use it;
- Create _Github Issues_ and assign them _assignees_;
- Comment on and close a _Github Issue_;

## What is a _Github Issue_?

In the context of Github, an _issue_ is a feature that allows users to track tasks, bugs, and feature requests for a specific repository. It's a great way to quickly get an overview of the project and plan and prioritize your workflow accordingly. _Issues_ are also one way that project members can communicate about the project in the repository and track its progress. The ability to create _issues_ comes with each repository created and in addition to communication, _issues_ also form part of the project documentation.

An _issue_ is usually opened by a user and can be assigned to one or more other users who might work on that problem. An _issue_ can contain a **title**, **description**, **labels**, and other metadata such as **priority** or the **person** responsible for fixing it.

Github allows the use of pre-created templates for opening common _issues_ such as _bug reports_ and _feature requests_. Templates can also be created according to the needs of your project.

## Why Use _Github Issues_?

GitHub _issues_ can be used for various purposes, such as:

- Assigning tasks
- Setting deadlines
- Tracking bugs in software projects
- Monitoring feature/attribute requests and enhancements
- Discussing and coordinating work among a team of developers
- Seeking or offering support for a specific repository or project

_Issues_ can be searched and filtered based on various criteria, such as _Issue_ **number**, **title**, **author**, **label**, and **status**. They can also be **commented on** and **updated** to reflect **changes** in the status of the tracked work. Using the _issue_ search is highly recommended to avoid creating duplicate _issues_ (i.e., creating _issues_ with the same or similar content in larger projects). Other similar tools usually have an automatic duplicate detection system, unfortunately, Github Issues does not offer this feature. However, Github allows users themselves to report _issue_ duplicates and group similar problems together. To do this, use `duplicate of #*issue* nr`, `duplicate pull request`, or `duplicate *issue*` keywords when commenting or replying.

## Best Practices for Writing _Issues_

- Keep titles short and to the point
- In the content, describe the background (_context_), present the problem or idea, and propose a solution or next step
- Use _labels_, but not too many at once
- For clarity, use _markdown_ language for formatting (lists, emphases, images, links, etc.)
- Include others – _@mentions_ and _assigned to_
- Before submitting an _issue_, make sure the same/similar problem has not already been raised – use the search option!
- Distinguish between an _issue_ and a _discussion_ – GitHub Discussions are a better option for more open-ended discussions
- Close resolved _issues_ to avoid confusion

## Example of a Well-Structured _Issue_

![good practice example](https://wiredcraft.com/images/posts/how_we_write_our_github_issues_2.png)

A specific title, background description, involving people, and the next step proposed.

## Example of a Poorly Written _Issue_

![bad example](https://wiredcraft.com/images/posts/how_we_write_our_github_issues_1.png)

Title too long, content too general.

## Exercises

To practice what you have learned in this topic, do the following:

- Create an `Issue` in one of your repositories, add a title, description, and some labels
- Add an `assignee` to the `Issue`
- Add a comment to an `Issue` directed at you
- Close the `Issue` you created if it has received any comments
