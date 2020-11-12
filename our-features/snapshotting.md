---
description: >-
  A key feature for reproducible research and a more documented, tractable
  workflow
---

# Snapshots

This page describes snapshots conceptually. 

## What is snapshotting?

Snapshotting is a key feature of Nuvolos. Snapshotting creates a _complete, immutable, persistent, restorable and shareable_ copy of the current state of your workflow. Snapshotting is a key component to speeding up dissemination of scientific results.

### Completeness

Nuvolos ensures that the copy of the current state is complete. This means that your files, database tables, application data and application setting and dependencies all get saved as a unit.

### Immutability

Nuvolos ensures that the copy created of your work cannot be modified after the fact.

### Persistence

Nuvolos ensures that the copy created by snapshotting will be available either until a project gets explicitly deleted or as long as the subscription exists.

### Restorability

Nuvolos makes it possible to restore a snapshot to the current state of a project. This makes it possible to pick up work at a later time without additional due diligence needed.

### Shareability

Nuvolos makes it possible to share a snapshot with a colleague or a student. 

## Why is snapshotting useful?

To demonstrate usefulness of the feature, consider the following use cases:

### Reproducible Research

One of Nuvolos' goals is to help the scientific community advance towards an era of completely reproducible research. By creating a snapshot of your work, you can be sure that your code will produce the exact same results, no matter who runs it.

### Setting up a class

You can set up a class by first building and testing your material. Once you are done, you can create a snapshot and then distribute this snapshot to all students taking the class with you. The students will receive the entire computing environment just as you have set it up, so they can get to work immediately.

### Onboarding a new member to a research project

Once the new research project members are invited to Nuvolos, you can distribute the current state of your project to them and they can start their work, without the need to spend valuable time worrying about setting up their infrastructure just the right way.

### Create an audit trail for assignments

Students also have the ability to take snapshot of their work. A snapshot is always time-stamped, and greatly simplifies handling in assignment. The student does not need to worry whether their work is reproducible, and the educator does not have to worry about managing a myriad of files and e-mails.

