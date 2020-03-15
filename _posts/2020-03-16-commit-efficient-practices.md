---
layout: post
title: Some efficient practices on how to commit code
date: 2020-03-16
---

The following is a more of a guideline on how to commit your code and why I think so.
I am assuming Git as the version control, that being said, the following could be used for any Version Control System.

Design Principles:

- I want to use the same git workflow as much as possible , on different projects.
- My pull requests should be easy to review and debug.
- Have an easy to setup my workflow and configure.
- Ensure linting and security.
- Should be able to make changes to my workflow easily.

Use :
-  ` git diff --check `, which identifies any possible whitespace errors and lists them for you. This can be added as a 
git hook potentially.

-  Commit messages should be around 50 to 60 characters long, at max. Similar to how one limits 120 characters perline 
when writing code.

- Make seperate commits for logically seperate changes.

- Use imperative tone , for your commit messages.
    - Example : `Make IndexController check for token` over `Made chnages to ensure IndexController checks for token`
    - Reason: More concise  and the intent of the chnage is understood right away.

- Using git config i.e. `.gitconfig` file , to set the up required info. Such as :
    - GPG signature, Author info
    - Reason : To make the commit more readbale and secure. This totally depends on the usecase.

- Check if any sensitive info is checked in as part of the commit. One should have an automated way, of checking this type of change.
    - Reason :  So that the security exposure is minimised and when automated, the cost of setup is minimal going forward.
    - It's also scalable, when working in a team and easier to enforce rules.

- Automate as much as of the git workflow, as possible. Ensure the onborarding of this workflow is simple or atleast not too cumbersome.
 You can make incremental chnages over time.


Sources I have used for reference: 

- [Git Documentation for Submitting patches](https://git.kernel.org/pub/scm/git/git.git/tree/Documentation/SubmittingPatches?id=HEAD#n133)
- [Dotfiles](https://dotfiles.github.io)


For any feedback you can tweet me at [@vaikuntj](https://twitter.com/vaikuntj) .