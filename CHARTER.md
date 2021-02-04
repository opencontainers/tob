# Open Container Initiative Charter v1.2+DRAFT

| Version   | Notice Date | Effective Date | Changes                                  |
| --------- | ----------- | -------------- | ---------------------------------------- |
| 1.0       | 2015-11-13  | 2015-11-13     | *Initial release.*                       |
| 1.1       | 2020-05-06  | 2020-06-05     | &bull; *(Section 1)* Remove scope table. |
| 1.2       | 2020-06-04  | 2020-07-04     | &bull; *(Section 1)* Simplify mission.   |
| 1.2+DRAFT |             |                | &bull; *(Section 2)* Simplify OCI Project definition and clarify scope. |
| 1.2+DRAFT |             |                | &bull; *(Section 2)* Restrict out-of-specification features in OCI Reference Implementations. |
| 1.2+DRAFT |             |                | &bull; *(Section 5)* Simplify TDC description and enshrine all maintainers of OCI Projects as TDC Maintainers. |
| 1.2+DRAFT |             |                | &bull; *(Section 6)* Unify TOB voting rules to always require a qualified super-majority for decisions. |
| 1.2+DRAFT |             |                | &bull; *(Section 6)* Update TOB procedures, codify election process, and remove outdated sections.  |
| 1.2+DRAFT |             |                | &bull; *(Section 6)* Add No-Confidence Motions to allow the Maintainers Coalition to dissolve the TOB.  |
| 1.2+DRAFT |             |                | &bull; *(Section 6)* Describe the procedure for by-elections.  |
| 1.2+DRAFT |             |                | &bull; *(Section 12)* Formalise changelog, version numbers, and draft charter versions. |

> **NOTE**: The "notice date" is the date at which OCI Members were given
> notice regarding the relevant changes, and the "effective date" is the date
> when the respective version of the Charter came into effect -- in accordance
> with Section 12 (a) of this Charter.

## 1. Mission of the Open Container Initiative ("OCI")

The Open Container Initiative provides an open source technical community
within which industry participants may easily contribute to building
vendor-neutral, portable and open specifications, reference implementations,
and tools that deliver on the promise of containers as a source of application
portability backed by a certification program.

The Open Container Initiative does not seek to be a marketing organization,
define a full stack or solution requirements, and will strive to avoid
standardizing technical areas undergoing innovation and debate.

## 2. OCI Projects

a. The OCI will maintain a collection of projects ("OCI Projects") to execute
   its Mission as outlined in Section 1 of this Charter.

b. Each OCI Project must belong to a category (hereafter "Project Category" in
   this Section), meaning it must be categorised as:

   - i. a specification ("OCI Specification"), which describes an industry
     standard that the OCI maintains, which must be within the scope of the
     OCI's Mission as described in Section 1 of this Charter; or
   - ii. a reference implementation ("OCI Reference Implementation"), which
     implements an OCI Specification; or
   - iii. a conformance test suite ("OCI Conformance Suite"), which can be used
     to validate whether a (possibly third-party) project implements an OCI
     Specification correctly, and may be used as a basis for judging
     conformance to an OCI Specification (notwithstanding Section 2 (c) of this
     Charter); or
   - iv. a library ("OCI Library"), which is small, reusable, and can assist
     other projects in implementing an OCI Specification.

c. The initial OCI Projects shall be:

   - i. an OCI Specification for container runtimes ("OCI Runtime
     Specification"); and
   - ii. an OCI Reference Implementation of the OCI Runtime Specification
     ("runc").

d. When an OCI Project claims that a feature is provided from an OCI
   Specification, all of its constituent parts shall comply with the OCI
   Specification. Section 2 (g) of this Charter notwithstanding, an OCI Project
   may have additional capabilities that are not reflected in the associated
   OCI Specification. In this case, it is understood that the OCI Specification
   (and any associated OCI Conformance Suites) are the standard for judging
   compliance, not the OCI Project. For the avoidance of doubt, this means that
   if there is a real or perceived conflict between an OCI Specification and an
   OCI Conformance Suite, the OCI Specification has precdence as the basis for
   conformance.

e. The set of OCI Projects may be modified by the TOB using the process
   outlined in Section 2 (e) of this Charter, so long as such modifications are
   in the spirit of this Charter and are in accordance with Section 2 (a) of
   this Charter.

f. Any TDC member may bring forward a proposal to the TOB for a new or existing
   project to be included in the set of OCI Projects. Approval of a new OCI
   Project requires the TOB to decide in favour of the proposal, following the
   process outlined in Section 6 (o) of this Charter. For the avoidance of
   doubt, any project (once included in the OCI Projects) will be governed
   under the rules of this Charter.

g. A project need not be contributed to the OCI in order to be deemed compliant
   with an OCI specification, nor need it only implement the set of features
   defined in an OCI Specification. For the avoidance of doubt, a project can
   be compliant with an OCI Specification even if:

   - i. it differs substantially from any associated OCI Reference
     Implementation; or
   - ii. it is not an OCI Project; or
   - iii. it is licensed differently to any OCI Project, including if it is
     licensed under a proprietary license; or
   - iv. it implements features which are not included in the associated OCI
     Specification.

h. In order to facilitate Section 2 (g) of this Charter,

   - i. OCI Specifications:

     a. must have a strong bias to exclude items from the specification in
        technical areas undergoing significant innovation and debate, especially
        if those areas are likely to be the basis of differentiation between
        competing implementations; and

     b. must establish a clear scope of the specification (hereafter
        "Specification Scope" within this Section), which once established may
        only be changed via a TOB decision, following the process outlined in
        Section 6 (o) of this Charter.

   - ii. OCI Reference Implementations:

     a. may implement functionality outside of the Specification Scope of the
        associated OCI Specification, but any such features must not compromise
        compliance with the OCI Specification; and

     b. must not implement functionality within the Specification Scope of the
        associated OCI Specification, without clearly marking such features as
        experimental and subject to change in response to any future
        developments within the OCI Specification.

   - iii. OCI Conformance Suites:

     a. must only test for strict conformance with the OCI Specification
        (meaning that they must not place requirements on any features
        permitted under Sections (g)(i) and (g)(iv) of this Charter); and

     b. must not emit a conformance test failure for any optional features
        within an OCI Specification (though they may produce a non-fatal
        warning if the tested project does not follow a specific recommendation
        given by the OCI Specification).

i. Both the Project Category and Specification Scope of each OCI Project will
   be maintained in [the TOB's repository](https://github.com/opencontainers/tob).
   Changing an OCI Project's category requires a TOB decision in favour of the
   change, following the process outlined in Section 6 (o) of this Charter,
   with thirty (30) days’ notice to the OCI Members before taking effect.

j. Due to historical considerations, the OCI Runtime Reference Implementation
   ("runc") project is exempt from the requirements of Section 2 (h)(ii)(b) of
   this Charter. For the avoidance of doubt, no other OCI Reference
   Implementations are granted such an exemption.

## 3. Membership.

a. The Open Container Initiative shall be composed of:

   - i. OCI Members: Corporate Members of The Linux Foundation that have
     executed an OCI Membership Agreement to sponsor the activities of the OCI
     Community and a certification program through a Trademark Board;
   - ii. an open source, Technical Developer Community (“TDC”), open to any
     individual, whether an employee of an OCI Member or not;
   - iii. a Technical Oversight Board (“TOB”); and
   - iv. A Trademark Board.

b. OCI Members shall be entitled to:

   - i. participate in OCI Trademark Board meetings, OCI Projects, and any
     other activities sponsored by the OCI;
   - ii. identify their company as a member or participant in the OCI;
   - iii. use any approved OCI membership logo in compliance with guidelines
     established by the LF Trademark Board
   - iv. vote in all decisions of the OCI Trademark Board.

c. OCI non-Member Participants shall be entitled to fully participate in all
   OCI Projects subject to the terms of this Charter and any policies adopted
   by the Trademark Board.

## 4. Trademark Board

a. The Trademark Board shall be composed of one representative appointed by
   each OCI Member. A Member may appoint an alternative representative for any
   meeting.

b. Trademark Board meetings may be held in-person or via electronic
   conferencing. The Trademark Board shall establish its own meeting schedule
   and operating procedures.

c. Quorum for holding meetings shall be established when a simple majority of
   Trademark Board representatives is present.

d. The intention is for the OCI to operate by consensus. However, if consensus
   cannot be achieved, the Trademark Board shall vote on a decision. Votes
   either at meetings, via email or electronic voting service, shall be based
   on a one vote per Active Member basis, requiring a simple majority of votes
   cast to pass. An abstain vote equals not voting at all. An Active Member is
   defined as any OCI Member whose representative attended (including by
   telephone or electronic conference or meeting) at least one of the last four
   Trademark Board meetings. An alternative representative’s attendance counts
   as participation for determining whether a Member is an Active Member.

e. The Trademark Board is intended to provide a minimalist governance structure
   around the development and use of the OCI trademarks and shall be
   responsible for:

   - i. creating the OCI trademarks associated with OCI Projects (including the
     OCI Specifications), the Open Container Format (OCF), or OCI certified
     solutions.
   - ii. creating a certification program establishing the requirements for
     achieving the status of an “OCI Certified Solution” and defining the terms
     for using any OCI trademark(s) for an OCI Certified Solution;
   - iii. approving the use of OCI funds for specific trademark a trademark
     registration program, and for enforcement actions, if any, that may be
     advisable;
   - iv. creating and approving a budget directing the LF how to use the OCI
     funds raised from all sources of revenue;
   - v. organizing and directing marketing initiatives including, but not
     limited to, press releases, website updates, and creation of collateral
     and branding materials;
   - vi. electing a Chair of the Trademark Board each January, or at another
     time of its choosing by an approved vote of the Trademark Board, to
     preside over meetings, set agendas, authorize budgeted expenditures and
     managing any day-to-day operations; and
   - vii. voting on other decisions or matters that may come before the
     Trademark Board, including adopting policies related to the scope of the
     Trademark Board which shall be documented for Members.

f. Any certification program established by the OCI Trademark Board must
   support a vendor-neutral process and requirements, including specifically,
   the ability for solutions to be certified on multiple operating systems and
   usable in multiple environment implementations.

g. Any issues that cannot be resolved by the Trademark Board shall be referred
   to The Linux Foundation for resolution.

h. For avoidance of doubt, OCI membership does not convey any rights to
   directly influence the technical direction of any OCI Project. That
   influence will come through code and specification contributions to the
   technical projects.

## 5. Technical Developer Community (TDC)

a. The OCI shall host and support the participation of a technical development
   community ("TDC"), encompassing all OCI Projects. The TDC consists of two
   groups:

   1. TDC Contributors, membership of which shall be open to any developer, end
      user or subject matter expert that chooses to participate in the
      activities of any OCI Project, regardless of whether the participant is
      employed by an OCI Member company so long as their contributions and
      conduct comply with this Charter.
   2. TDC Maintainers (hereafter "Maintainers"), which are the set of
      maintainers for a given OCI Project (as listed in the top-level
      MAINTAINERS file of the OCI Project). For the avoidance of doubt, all
      Maintainers are also necessarily TDC Contributors. In addition:

      - i. an individual may only become a Maintainer of an OCI Project
        after approval by whatever procedure that OCI Project's Maintainers
        have established under Section 5 (b)(iii) of this Charter; and
      - ii. only the Maintainers of an OCI Project may modify the set of
        Maintainers for that OCI Project. No OCI Member, the TOB, the
        Maintainers of different OCI Project, nor the Trademark Board may
        modify the set of Maintainers for a given OCI Project (except in cases
        where an existing Maintainer's contributions or conduct have not
        complied with this Charter); and
      - iii. the collection of Maintainers for all OCI Projects shall be
        referred to in this Charter as the "Maintainership Coalition".

b. The Maintainers of each OCI Project have a responsibility to create,
   maintain and enforce governance guidelines for the TDC of their OCI Project,
   which shall be posted visibly for the TDC. The guidelines shall cover:

   - i. establishing and defining roles and responsibilities (at a minimum, a
     role for committers or maintainers authorized to commit code to the
     codebase); and
   - ii. defining the process or requirements to take on a role in the TDC
     (including but not limited to how to become a contributor and how to
     become a maintainer); and
   - iii. the process by which participants in the TDC may give up or be
     revoked of their roles (including but not limited to how to remove
     maintainers);
   - iv. the rules for decision making in the TDC; and
   - v. any workflow or processes participants are expected to follow in
     making or merging contributions; and
   - vi. the procedure for approving and publishing releases of the OCI
     Project.

c. The TDC has an established scope of work for all OCI Projects. For each OCI
   Project, the TDC has a responsibility to:

   - i. ensure that the OCI Project adheres to the general requirements for
     OCI Projects and the specific requirements for their project's Project
     Category, as outlined in Section 2 of this Charter; and
   - ii. ensure that the OCI Project incorporates and aligns with the OCI
     Values, as defined in Section 7 of this Charter; and
   - iii. ensure that the OCI Project follows and adheres to the OCI IP Policy,
     as outlined in Section 8 of this Charter. Any issues of non-compliance
     with the OCI IP Policy shall be immediately referred to The Linux
     Foundation; and
   - iv. create and maintain the OCI Project such that it is portable across
     all major, compliant operating systems and platforms without artificial
     technical barriers; and
   - v. engage end users for feedback or input on the OCI Project, including,
     but not limited to, relating to usability.

d. In addition to the responsibilities outlined in Section 5 (b) of this
   Charter, Maintainers of OCI Specifications have a responsibility to:

   - i. attempt to harmonize the OCI Specification with other proposed
     standards, including, but not limited to, the AppC specification; and
   - ii. ensure that the scope of technologies promulgated and proposed as
     elements of the OCI Specification are those that are sufficiently
     widespread and sufficiently mature and stable so as to warrant
     establishment in the specification; and
   - iii. in addition to Section 5 (b)(vi) of this Charter, require a qualified
     super-majority vote of Maintainers of the OCI Specification in order to
     approve any release of the OCI Specification.

e. In addition to the responsibilities outlined in Section 5 (b) of this
   Charter, Maintainers of OCI Conformance Suites have a responsibility to
   create and maintain test cases that shall serve as the testing functions for
   achieving certification as an OCI Certified Solution.

f. Notwithstanding Section 2 (i) of this Charter, the TDC Members and
   Maintainers shall set the technical direction of the OCI Projects, with
   minimal interference by the TOB. However, any issues that deal with failure
   to follow established technical governance, issues that impact multiple OCI
   Projects or specifications, or conflicts that cannot be resolved within the
   TDC shall be referred to the TOB using the procedure outlined in Section 6
   of this Charter. Once an issue is referred to the TOB, the TOB is empowered
   to resolve it (though such resolutions should be made in consultation with
   the relevant Maintainers or the Maintainership Coalition).

g. The TDC will only accept influence through contribution. The primary means
   for any organization to influence the technical direction of the OCI
   Projects is via contribution as TDC Members or service as Maintainers. OCI
   Members specifically disclaim any right to influence technical direction
   either on the basis of their financial contributions or their existence as
   OCI Members.

## 6. Technical Oversight Board (TOB)

a. The OCI shall have a Technical Oversight Board ("TOB"), which is responsible
   for managing conflicts, violations of procedures or guidelines and any
   cross-project or high-level issues that cannot be resolved by the TDC. The
   TOB shall not dictate or interfere with the day-to-day work of individual
   OCI Projects or their decisions.

b. The TOB shall be responsible for adopting any policies related to the scope
   of the TOB and ensuring they are documented publicly.

c. The TOB shall operate transparently with any discussions and mailing lists
   open to the community. The TOB may choose to set up a private discussion or
   mailing list if a situation warrants a private discussion (e.g. removing a
   TOB member, addressing a legal issue), but the general expectation is that
   the TOB’s discussions and decisions are open to the OCI Community. If a
   decision is made in private, the TOB must follow all quorum and voting
   requirements as normally required and shall be responsible for notifying the
   OCI Community of the decision and rationale. Any private meeting of the TOB
   shall also require a representative from The Linux Foundation to ensure this
   option is not being abused.

d. The TOB shall be composed of nine (9) individuals elected by the
   Maintainership Coalition for their expertise, contribution to the
   advancement of container technologies and are considered to be thought
   leaders in the OCI ecosystem. A TOB member is elected as an individual and
   not as a representative of his or her employer. TOB members may not
   designate alternative representatives.

e. An individual is incapable of being a member of the TOB if they at any point
   during their tenure they:

   - i. are not a member of the TDC; or
   - ii. become unable to exercise their duties as a TOB member; or
   - iii. are employed by the same entity or affiliate as two (2) or more other
     TOB members. Affiliates shall be defined as entities owning 50% or more of
     an entity, or owned by or under common ownership with each other.

f. TOB members shall be split into two (2) groups counting four (4) and five
   (5) members each, both serving for a term of two (2) years on a staggered
   basis, with an election being held each year alternating between which
   group's seats are up for election.

g. The TOB membership shall be chosen through a nomination and election
   process, organised by the Executive Director. The procedure for nomination
   and election of seats shall be:

   1. The Executive Director shall publicly call for nominations no less than
      four (4) weeks before the expiry of the current group of TOB seats, or
      immediately if the seats have already become vacant. The nomination
      period shall last a minimum of two (2) weeks.
   2. Each member of the Maintainership Coalition may privately nominate up to
      two (2) candidates, with no more than (1) nominated candidate being
      employed by the same entity or affiliate as the Maintainer. Affiliate
      shall be defined as in Section 6 (e)(iii) of this Charter. Information
      about which member nominated which candidate must remain private.
   3. The Executive Director shall call for a vote for the TOB seats with all
      nominated candidates (who are elligible under Section 6 (e) of this
      Charter) being included as choices on the ballot, using the voting
      procedure prescribed in Section 6 (j) of this Charter. Each member of the
      Maintainership Coalition is entitled to only one (1) vote, regardless of
      whether the individual is a Maintainer of a single or multiple OCI
      Projects. The voting period shall last a minimum of two (2) weeks.
   4. Upon the conclusion of the election, the members-elect shall become TOB
      members upon expiry (or vacancy) of the TOB seats.

h. Notwithstanding Section 6 (f) through (g) of this Charter, the initial TOB
   shall have its four (4) member group only serve a term of one (1) year and
   will be nominated and elected by OCI Members, with each OCI Member being
   permitted to nominate one (1) candidate for election and being given one (1)
   vote. For the avoidance of doubt, this procedure only applies to the initial
   TOB, and the five (5) member group of the initial TOB shall serve a term of
   two (2) years and be nominated and elected through the procedure defined in
   Section 6 (g) of this Charter.

i. After each election the TOB shall, before the dispatch of any other
   business, elect one (1) TOB member (using the procedure described in
   Section 6 (g) of this Charter) to be the TOB Chair, who shall hold that
   position for a term of one (1) year. In the event of a tie vote, a random
   selection process (such as a fair coin toss) shall be used to determine the
   winner. The TOB Chair shall have the responsibility to call meetings of the
   TOB and set TOB meeting agendas with input from TOB members.

j. Elections of TOB members and the TOB chair shall be run by the Executive
   Director, using the Condorcet-IRV method through the [Condorcet Internet
   Voting Service](https://civs.cs.cornell.edu/). Upon the completion of any
   vote using this procedure, the Executive Director must announce the results
   of the vote publicly.

k. If at any point a TOB member becomes incapable of holding their seat (as
   defined in Section 6 (e) of this charter), their seat shall become vacant
   and a by-election shall be called using the procedure described in Section 6
   (g) of this Charter to fill the vacant seat. The newly elected TOB member
   shall serve the outgoing TOB member's remaining term. For the avoidance of
   doubt, if more than one TOB member becomes incapable of holding their seat
   (such as a merger resulting in more than two TOB members being employed by
   the same entity or affiliate as described in Section 6 (e)(iii) of this
   Charter), all incapable TOB members' seats will become vacant simultaneously
   and only one by-election will be held to fill all vacant seats.

l. The TOB shall meet on an as-needed basis to discuss any agenda set by the
   TOB Chair, who may set such an agenda at any time if they determine a
   meeting is necessary. Members of the TDC outside of the TOB may attend and
   participate in TOB meetings, but cannot vote on motions nor raise issues
   which are not part of the meeting agenda.

m. In the case of any issues being directed to the TOB, the TOB Chair must call
   a meeting in a timely manner with an agenda including the issues directed to
   the TOB, so that the TOB may resolve them. An issue may be directed to the
   TOB from:

   - i. the Maintainers of one (1) or more OCI Projects, by a qualified
     majority vote of the set of Maintainers of the given OCI Projects, for an
     issue involving only the given OCI Projects; or
   - ii. the Maintainership Coalition, by a qualified majority vote; or
   - iii. the TOB via a decision made using the process outlined in Section 6
     (o) of this Charter; or
   - iv. the TOB Chair if they determine a meeting is necessary.

n. Issues should be referred to the TOB sufficiently in advance of a meeting to
   provide an appropriate time for TOB members to evaluate the issues, and the
   positions of the TDC, the positions of users, as well as sufficient time to
   explore compromise solutions. It is expected an appropriate review should
   require at least a two (2) week review period, though it is recognized some
   time-critical circumstances may call for a shorter review (such as security
   issues).

o. TOB meetings may be held in-person or via telephone or electronic
   conferencing. Quorum for holding meetings shall be established when
   two-thirds of TOB members are present. If the TOB is unable to form a
   quorum, the TOB Chair must call subsequent meetings in a timely manner with
   the same agenda until a quorum is formed.

p. The intention is for the TOB to operate by consensus. However, if consensus
   cannot be achieved, the TOB shall vote on a decision. All TOB votes, either
   at TOB meetings, via email or electronic voting service, shall pass with a
   qualified super-majority (a two-thirds vote of the entire TOB membership in
   favour of the motion in question), on a one (1) vote per TOB member basis.
   For the avoidance of doubt, an abstain vote (or not voting) equals a vote
   against the motion in question. If a vote is conducted outside of a TOB
   meeting, the vote will be organised by the Executive Director and must have
   a clearly established deadline at which point the votes will be tallied and
   announced by the Executive Director. If any TOB seats have become vacant (as
   outlined in Section 6 (k) of this Charter), they are not counted for the
   purposes of the qualified super-majority.

q. Any issues that cannot be resolved by the TOB shall be referred to the Linux
   Foundation Executive Director for mediation, and, if necessary, for
   resolution by The Linux Foundation Board of Directors.

r. If the Maintainership Coalition feels that the TOB does not represent their
   interests, they may raise a No-Confidence Motion by a qualified majority
   vote. Votes for No-Confidence Motions must be announced publicly and will be
   administered by the Executive Director using the procedure in Section 6 (j)
   of this Charter. If a No-Confidence motion is passed, then the entire TOB is
   immediately dissolved and an election is held to replace all of the TOB
   seats.

s. The procedure for an election under Section 6 (q) of this Charter is
   identical to that of Section 6 (g) of this Charter, except that the four (4)
   member group of the TOB will only hold their seat for one (1) year in order
   to maintain the staggered terms outlined in Section 6 (f) of this Charter.
   The four (4) member group will be chosen as being the least-favoured choices
   in the election who cleared the threshold for election. In the case of any
   ambiguity (such as a tie for 5th place), a random selection process (such as
   a fair coin toss) shall be used to select which member-elect will be part of
   the four (4) member group.

t. In order to avoid abuse of No-Confidence Motions, they cannot be announced
   within two (2) weeks before or after a TOB election nor within ninety (90)
   days of a previous No-Confidence Motion (even if the previous motion was not
   successfully passed).

## 7. OCI Values.

The TDC and TOB shall strive to reflect and adhere to the following values
(“OCI Values”) for OCI Projects:

a. Composable. All tools for downloading, installing, and running containers
   should be well integrated, but independent and composable. A container
   runtime should not be bound to clients, to higher-level frameworks, etc.

b. Portable. The runtime standard should be usable across different hardware,
   operating systems, and cloud environments.

c. Secure. Isolation should be pluggable, and the cryptographic primitives for
   strong trust, image auditing and application identity should be solid.

d. Decentralized. Discovery of container images should be simple and facilitate
   a federated namespace and distributed retrieval.

e. Open. The format and runtime should be well-specified and developed by a
   community. OCI encourages independent implementations of tools to be able to
   run the same container consistently. Within the OCI Community, code
   development leads specification development, rather than vice-versa. The OCI
   Community seeks rough consensus and running code.

f. Minimalist. The OCI Specifications should aim to do a few things well, be
   minimal and stable, and enable innovation and experimentation above and
   around it.

g. Backward compatible. The first version of the OCI Specification should
   strive to be backwards compatible with the initial container image format
   and runtime contribution. OCI Specifications and code should strive to be
   backward compatible with the prior releases of the OCI Specification.

## 8. OCI IP Policy.

a. All new inbound contributions to OCI will be made under the Apache License,
   Version 2.0 (available at http://www.apache.org/licenses/LICENSE-2.0)
   accompanied by a Developer Certificate of Origin sign-off
   (http://developercertificate.org). All contributions by Member employees
   will bind their employers in accordance with this policy, including the
   patent and copyright license grants in the Apache License, Version 2.0.

b. All outbound code and documentation will be made available under the Apache
   License, Version 2.0.

c. If an alternative inbound or outbound license is required for compliance
   with the license for a leveraged open source project, is otherwise required
   to achieve OCI’s mission or is in the best interests of OCI, the TOB may
   approve the use of an alternative license for inbound or outbound
   contributions on an exception basis. Please email tob@opencontainers.org to
   obtain exception approval.

d. Upon finalization and release of a new version of any OCI Specification, the
   Executive Director will notify all Members in writing using the contact
   information provided in Exhibit A. As set forth in Section 12 of this
   Charter, Members may resign from membership in OCI at any time within thirty
   (30) days following such notification to avoid undertaking further
   obligations with respect to such specification. All Members on the date
   thirty (30) days following such notification will, without further action,
   be subject to the obligations set forth in the Open Web Foundation Final
   Specification Agreement (OWFa 1.0) (Patent Only) with respect to such
   specification.
   http://www.openwebfoundation.org/legal/the-owf-1-0-agreements/owfa-1-0—patent-only

e. On the effective date of their membership, all Members will, without further
   action, be subject to the obligations set forth in the OWFa 1.0 (Patent
   Only) with respect to the current and one immediately prior version of all
   OCI specifications, a version being a numerically designated version of the
   specification formally released following the thirty day period provided for
   in (d) above. Each new version of the specification will be designated by a
   change in the number to the left of the decimal point (x in an x.y format
   where y designates interim update releases).

## 9. Antitrust Guidelines

a. All Members shall abide by The Linux Foundation Antitrust Policy available
   at http://www.linuxfoundation.org/antitrust-policy.

b. All Members shall encourage open participation from any organization able to
   meet the membership requirements, regardless of competitive interests. Put
   another way, the OCI shall not seek to exclude any entity or any individual
   from OCI membership or OCI Project participation based on any criteria,
   requirements or reasons other than reasonable and appropriate criteria and
   requirements approved under this Charter and applied in a nondiscriminatory
   fashion to all.

## 10. Budget

a. The Trademark Board shall approve an annual budget and never commit to spend
   in excess of OCI membership and other OCI directed funds raised byThe Linux
   Foundation from all sources, including OCI membership fees. The budget and
   all OCI activities shall be consistent with the non-profit mission of The
   Linux Foundation.

b. So long as funds are sufficient, the OCI Budget shall include funds for a
   parttime program manager, or at the Trademark Board’s discretion, an
   Executive Director, to assist OCI with project management, organizing
   meetings and assisting in driving initiatives of the Trademark Board, TDC or
   TOB.

c. The Linux Foundation shall provide regular reports of spend levels against
   the budget.

d. The Linux Foundation shall have custody of and final authority over the
   usage of all OCI fees, funds and other cash receipts. To the extent that OCI
   acquires ownership in any intellectual property, ownership shall reside in
   The Linux Foundation.

## 11. The Linux Foundation General Rules and Operations.

The OCI, and as appropriate, its Members and participants, shall operate under
such rules and policies as may from time to time be applicable to Linux
Foundation hosted projects, and, in addition, shall:

a. demonstrate plans and the means to coordinate with the TDC, including on
   topics such as branding, logos, and other collateral that will represent the
   OCI Community;

b. engage in a professional manner consistent with maintaining a cohesive
   community, while also maintaining the goodwill and esteem of The Linux
   Foundation in the open source software community;

c. respect the rights of all trademark owners, including any branding and usage
   guidelines;

d. engage The Linux Foundation for all OCI press and analyst relations
   activities;

e. upon request, provide information regarding OCI Project participation,
   including information regarding attendance, to The Linux Foundation;

f. engage The Linux Foundation for creation and management of any websites
   relating directly to the OCI; and

g. operate under such rules and procedures as may from time to time be approved
   by the OCI and confirmed by The Linux Foundation Board of Directors.

## 12. Amendments and Notice

a. This Charter may be amended by a TOB decision using the process outlined in
   Section 6 (o) of this Charter, subject to veto by The Linux Foundation Board
   of Directors for reasonable cause, with thirty (30) days’ notice to the OCI
   Members before taking effect.

b. A Member may resign within such thirty-day notice period, or within the
   period provided for in Section 8 (d) of this Charter, to avoid undertaking
   any obligations imposed by any such amendment, or further obligations with
   respect to a specification, on a going forward basis. Such resignation will
   not have any effect on commitments made by the OCI Member or participant
   during the term of membership. Resignation may be made by email to the
   Executive Director of the Linux Foundation.

c. Each version of this Charter will have a distinguishing version number, with
   a changelog included in the preamble describing material changes to the
   Charter.

d. In order to facilitate collaborative development of this Charter, draft
   versions of this Charter may be indicated by the suffix "+DRAFT" added to
   the version number. These Charter versions are not enforceable, and the most
   recently published non-draft Charter remains in effect until a newer
   non-draft Charter is published. For the avoidance of doubt, amendments to a
   draft Charter still must go through the same process as amendments to a
   non-draft Charter (as described in Section 12 (a) of this Charter).
