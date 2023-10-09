# Git

- What is Git?
- Basic Git architecture (blobs, trees, commits, branches)
- Installing Git

## What is Git?

**Git** is a distributed version control system (*DVCS*) used to track changes in source code during software development. It's designed to handle everything from small to very large projects with speed and efficiency. **Git** provides a way for multiple developers to collaborate on the same codebase without interfering with each other.

Git was created by Linus Torvalds in 2005 for the development of the Linux kernel. Its adoption has grown rapidly, and it's now the dominant version control system in the software industry. It's used by companies like Google, Facebook, Microsoft, and Twitter to manage their codebases.

Here are the key aspects and features of **Git**:

- **Distributed System**: Unlike centralized version control systems where there's a single central repository, in **Git**, every developer's copy of the code is also a repository that can contain the entire history and version tracking capabilities. This ensures redundancy and makes operations like branching and merging extremely efficient.
- **Branching and Merging**: **Git**'s branching model allows developers to create isolated branches for feature development or bug fixes. These branches can then be merged back into the main branch, typically known as the 'master' branch.
- **History**: **Git** tracks the entire history of the project. Every commit is checksummed and retrievable, ensuring integrity and traceability.
- **Staging Area**: **Git** introduces a unique concept of a *staging area* or *index*. This is an intermediate area where commits can be formatted and reviewed before completing the commit.
- **Performance**: **Git** operations are performed locally, making it faster than many version control systems that rely on network operations.
- **Integrity**: **Git** uses a hashing algorithm called SHA-1 to checksum its data. This ensures the integrity of the version history.
- **Flexibility**: **Git** supports various workflows, from centralized to fully distributed, making it adaptable to different project needs.
- **Collaboration Platforms**: Platforms like *GitHub*, *GitLab*, and *Bitbucket* enhance **Git**'s collaborative capabilities by providing code hosting, pull requests, code reviews, and issue tracking.
- **Free and Open Source**: **Git** is free software distributed under the terms of the GNU General Public License version 2.

## Basic Git Architecture

Git has a unique architecture and data model that makes it efficient and powerful. Here's a breakdown of the basic components of Git's architecture:

- **Blobs**:
  - Represents the content of a file in Git.
  - A blob holds the file data but doesn’t contain any metadata about the file.
  - It's a binary large object and is identified by a SHA-1 hash of its content.

- **Trees**:
  - Represents a directory or folder in Git.
  - A tree object maps names to blobs or trees (essentially, it can reference other trees for subdirectories).
  - Like blobs, trees are identified by a SHA-1 hash.

- **Commits**:
  - Represents a particular point in the repository's history.
  - A commit points to a tree that captures the state of the repository at a certain point in time.
  - Contains metadata such as:
    - Author
    - Committer
    - Date
    - Commit message
  - Each commit also points to its parent commit(s), forming a linked list. This is what creates the "history" in Git. Merge commits can point to multiple parents.
  - Identified by a SHA-1 hash.

- **Branches**:
  - A moving pointer to a commit.
  - When you create a branch, Git creates a pointer to the commit you're currently on.
  - As new commits are created, the branch pointer automatically moves to point to the latest commit.
  - The default branch in most repositories is named "master" (though a shift towards naming it "main" has been observed recently).
  - Branches allow for divergent development, where features or experiments can be developed in isolation before merging them back into the main codebase.

This architecture, built around a directed acyclic graph of objects, is what allows Git to efficiently track changes, create branches, and merge histories. The use of SHA-1 hashes ensures the integrity and consistency of the repository across clones and versions.

## Installing Git

Latest version of Git and instructions for installation can be found from [git-scm.com](https://git-scm.com/book/en/v2/Getting-Started-Installing-Git).