# Proposing and discussing changes

## Introduction

The repository first objective is to give a place where community members can document their design ideas for WoT projects. 
The structure of this repository is heavily inspired by the [golang proposal system](https://github.com/golang/proposal).

Each design change must be discussed on a proposal issue. When needed, a document expressing the change motivations is merged inside this repository and referenced to the issue with a precise [naming schema](#design-documents).

Users must adhere to the [code of conduct](#code-of-conduct) of the community when discussing a proposal. Participating to the project evolutions needs to be a pleasant experience for everyone. We pursue a friendly, welcoming environment where everyone can express their ideas, always feeling at home. 

This document will describe the whole proposal workflow, from the opening of an issue, to the acceptance or refusal of design changes through discussion and engagement of the community. 

## What should be considered as a 'Proposal' ?

Proposals are suggestions for new projects to be developed under this open source effort or design changes to any of the wot-open-source-project repositories.

If you doubt the issue nature, and you feel it could be considered a design change to one project, you can always file a proposal.

## The proposal process

Each proposal can be either accepted or declined.
The process of reviewing them relies on the following workflow:

1. The proposal author *creates an issue* describing their proposed design changes.\
    At this point the issue **DO NOT** need documentation related to it

2. The discussion under the issue **must be managed by its author**. The discussion engagemnet will affect the proposal status which in the end can either be:
     - Accepted
     - Declined
     - In need of a design documentation file

3. If the discussion needs a more detailed description, the author must then provide more insights with the filing of a related [design documentation](#design-documents) in markdown format. The document should adress the concerns arised from the discussion thread on the issue, completing the information available at that moment. 

4. After the filing of the document, the discussion will continue under the proposal issue. In the end the proposal will be *accepted* or *declined* accordingly to the outcomes of the discussion itself.

A proposal can be flagged with other [statuses](#proposal-statuses) described more in depth in the [review workflow](#proposals-review).

After the proposal is accepted or declined (whether after step 2 or step 4),
implementation work proceeds in the same way as any other contribution.

## How to write a proposal

The issue titles must follow this schema:

```    
    proposal: <domain>: <title>
```

The `domain` refers to the project related to the proposal\
The `title` should be short and focused on the main proposal topic.

Issue descriptions must be clear and relevant to the core idea expressed in the title.

Proposal issues must be accompanied by the '*proposal*' tag, making them easier to track on issue pages.

## Design Documents

As noted above, when needed proposals can be deeper elaborated in a design document.

- The design doc should be added to the repository with a pull request to the `main` branch in [this current](https://github.com/web-of-things-open-source/proposal) repository
- The pull request should come from a branch whose name is composed as:
```
<Issue number>-<domain of the issue>-<short proposal title>
```
- The doc should be inserted into the `/design` folder, following the same schema above:
```
<Issue number>-<domain of the issue>-<short proposal title>.md
```
- if the document has media files, code examples or other files that are part of the documentation, they must be uploaded in a folder inside the `/design` path. The folder has the same name as the documentation file 

- The documentation must be written following [this template](./TEMPLATE.md).

- [Each sentence should start on a new line](http://rhodesmill.org/brandon/2012/one-sentence-per-line/)
so that comments can be made accurately and the diff kept shorter.

#### Example of a documentation upload

The user Mario made a proposal and now is asked to upload documentation related to it to deepen the analysis on the topic.

- *issue* -> "proposal: foo: Change bar api path" 
- *issue number* -> #42069
- *Documentation structure*:
```bash
/
└── design/
    ├── 42069-foo-change-bar-path.md
    └── 42069-foo-change-bar-path/
        ├── image-1.png
        ├── image-2.png
        └── code example.go
```

## Proposals Review

A group of the wot team holds “proposals review meetings”
periodically. 
The group will review the proposals and discuss the changes 
that can be advanced or declined.
The review is soley based on the engagement and general consensus under each issue discussion.

From each review meeting the team will change the status of the observed proposals to reflect the community decisions regarding them. This change will be noted on the corresponding issue pages by the team itself. 

Proposal issues are tracked in the
[Proposals project](https://github.com/orgs/web-of-things-open-source/projects/1/views/1) page where they are sorted by status.

All the review meetings will be documented in form of *minutes* collected inside the [minutes repository](https://github.com/web-of-things-open-source/minutes)

## Proposal Statuses
Each proposal can have other statuses other than *accepted* or *declined*, which alone define only the outcome of a proposal. 

The proposal statuses are:

- Accepted
- Declined
- Incoming
- Active
- Likely Accepted
- Likely Declined
- On Hold

### Incoming

New proposals are added to the ``Incoming`` column and tagged accordingly.

The monthly proposal review meetings aim to look at all the issues in the ``Active``, Likely Accept, and Likely Decline columns.

If there is some spare time, then proposals from ``Incoming`` are selected to be moved to ``Active``.

Holding proposals in ``Incoming`` until attention can be devoted to them is useful to have the focus on a small amount of issues rather than ending up cluttered by too many proposals.

### Active

Issues in the ``Active`` column are reviewed at each proposal meeting to watch for emerging consensus in the discussions.
The proposal review group may also comment, make suggestions,
ask clarifying questions, and try to restate the proposals to make sure everyone agrees about what exactly is being discussed.

### Likely Accept

If an issue discussion seems to have reached
a consensus to accept the proposal, the proposal review group
moves the issue to the ``Likely Accept`` column.

### Likely Decline

If a proposal discussion seems to have reached
a consensus to decline the proposal, the proposal review group
moves the issue to the ``Likely Decline`` column.
An issue may also be moved to ``Likely Decline`` if the
proposal review group identifies that no consensus
is likely to be reached and that the default of not accepting
the proposal is appropriate.

### Accepted

Short after a proposal moves to ``Likely Accept``, absent a change in consensus,
the proposal review group moves the proposal to the Accepted column.
If significant discussion happens during that time,
the proposal review group may leave the proposal
in ``Likely Accept`` for more time or even move the proposal back to ``Active``.

Once a proposal is marked ``Accepted``, the *Proposal-Accepted* label is applied and the issue is repurposed to track the work of implementing the changes.

### Declined

Short after a proposal moves to ``Likely Decline``, absent a change in consensus,
the proposal review group moves the proposal to the ``Declined`` column.
If significant discussion happens during that time,
the proposal review group may leave the proposal
in ``Likely Decline`` for more time or even move the proposal back to Active.
Once a proposal is marked ``Declined``, it is closed.

### On Hold

If discussion of a proposal requires design revisions or additional information the proposal review group moves it to the ``On Hold`` status. 

Once the requested documentation  is ready, anyone who can edit the issue tracker can move the
proposal back to the Active column.

## Help

If you need help with this process, please contact [@andrisciu](mailto:git@antoniazzi.dev)

## Code of Conduct
 
When discussing and actively partecipating in any form to the project each member of the community must adhere to the code of conduct.

----------

```
- Be friendly

- Be patient

- Be inclusive

- Be collaborative and critically constructive

- Be respectful and careful of the words you choose.
  Any form of discrimination, harrasment, menace or posting
  of sensitive content is not tolerated.
  
- Be open, and when others disagree with your opinion, try to
  understand why

```
-----------
