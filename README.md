# My good commit practices guide

### Introduction

I have relied on some already established patterns for writing commits, however, this guide has been created as a compilation of good practices for writing them.

### Step 1: Atomic commit
A commit need to be easily reversible, having everything needed for that fix or new funcionality in a single commit. Small commit are preferable, but each commit should work alone in insolation, solving a single problem, to be atomic. Sometimes an atomic commit ends up large, but an atomic commit should not solve more than one problem at the same time

For example, to resolve a bug, it is sometimes necessary to edit several files at the same time, and the commit remains atomic. However, if when solving this bug you want to take the opportunity to refactor something outside this context of the bug, improve documentation for another component, these things need to be in seperate commits, in order to be atomic.

### Step 2: New version or not
#### If a new version is to be generated, we have three options for the type of commit:

- <code>fix</code>: this commit has a correction or improvement to something that is currently in the public API of the project.
- <code>feature</code>: this commit is introducing new funcionality in the public API of the project
- <code>BREAKING CHANGE</code>: this commit is also one feature or one fix, but fot his new functionality or correction to be made,something that is currently in the public API of the project will have to be changed, making the user of our project, when updating the version, be able to have some manual work because of that.

#### If you don't generate any version:
- <code>build</code>: changes in settings and commands that generate the project build, examples: npm, tsconfig, angular-cli, webpack, etc.
- <code>ci</code>: changes in CI settings, examples: Jenkinsfile, artifactory, puppet, etc.
- <code>docs</code>: commit that contains ONLY documentation improvements.
- <code>perf</code>: small performance improvements in the application that do not need to generate new version
- <code>refactor</code>: improvements to the code that doesn't correct any bugs, does not add a new feature or generate breaking changes, which do not need to generate a new version.
- <code>style</code>: styles or cosmetic code improvements
- <code>test</code>: commit that contains ONLY new tests or corrects existing test.
- <code>chore</code>: if the edits to this commit are very generic and do not fit in ANY of the previous types, then this option can be used.

### Step 3: Write context changes and examples
In both changes (if you generate a new version or not) you should write the context to be clear what you worked on, for example:

#### Examples:
#### if you generate a new version:
- correction a bug in button component:
  - <code>fix(button-component): corrected text</code>
- adding a new input option in form:
  - <code>feature(form-component): new option for color variation</code>
- improvement in segment service:
  - <code>fix(segment-service): improved notification performance when changing segment</code>

#### if you don't generate any version:
- improving test coverage in navbar component:
  - <code>test(navbar-component): test coverage for output events</code>
- correcting formation errors in the segment service:
  - <code>style(service-component): standarized spacing between function blocks</code>
- chaning settings for the project's production build:
  - <code>build: new optimizations for React production build</code>

### Step 4: How to write messages correctly
Commit messages can be divided into two parts, the short(and mandatory) message is right after the type and context of the commit, and the long (and optional) message that is the specific description of the commit.

#### What to write in the message
When we write a confirmation message, we tend to erroneously describe in the short message the technical solution used, instead of giving a short description of the problem that is being solved, which is what really matters. If we want to specify the technical solution we can use the optional description message, for example:

#### Example 1:
<pre>
<code>fix(button-component): label update bug fixed

The connection between the aria-label when executing componentDidUpdate was solved</code>
</pre>

#### Example 2:
<pre>
<code>build: fixed demo app build command on linux

used shx to erase old dist fromt the demo app.</code>
</pre>

