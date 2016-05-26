---
layout: cover
title: "NIST SP 800-63-3 Digital Authentication Guideline"
description: "Public Preview for NIST Special Publication: SP 800-63-3 Digital Authentication Guideline"
---
<section class="home home-title" markdown="1">

# Digital Authentication Guideline: Public Preview

</section>
<section class="home home-about" markdown="1">
<div class="section-container" markdown="1">
<div class="section-content" markdown="1">

<ul class="audiences">
<li>
  <div>
    <a href="sp800-63-3.html"><img src="assets/800_63_3_doc.png" alt="SP 800-63-3" width="150px" height="150px"></a>
  </div>
  <h3><a href="sp800-63-3.html">SP 800-63-3</a></h3>
  <h6>Digital Authentication Guideline</h6>
</li>
<li>
  <div>
    <a href="sp800-63a.html"><img src="assets/800_63_3_Proofing.png" alt="SP 800-63A" width="150px" height="150px"></a>
  </div>
  <h3><a href="sp800-63a.html">SP 800-63A</a></h3>
  <h6>Identity Proofing & Enrollment</h6>
</li>
<li>
  <div>
    <a href="sp800-63b.html"><img src="assets/800_63_3_Authenticators.png" alt="SP 800-63B" width="150px" height="150px"></a>
  </div>
  <h3><a href="sp800-63b.html">SP 800-63B</a></h3>
  <h6>Authentication & Lifecycle Management</h6>
</li>
<li>
  <div>
    <a href="sp800-63c.html"><img src="assets/800_63_3_Federation.png" alt="SP 800-63C" width="150px" height="150px"></a>
  </div>
  <h3><a href="sp800-63c.html">SP 800-63C</a></h3>
  <h6>Federation & Assertions</h6>
</li>
</ul>

Welcome to the NIST SP 800-63-3 Public Preview!  We're excited to share the major transformation that this document has undergone, as well as collaboratively enhance and evolve the guidance as we head to a public draft later this summer.

## A few formalities

### Public preview vs public draft

If you've made it to this page, you can see we're approaching this a little differently by putting our work up on GitHub, rather than the "traditional" comment period for a NIST Special Publication (SP). We're calling it a public preview because some of our agency partners (and NIST itself) have formal processes for public drafts. Calling it a public preview is our way of letting everyone know those processes aren't in play. This lets us do things differently...

### A different cadence

This public preview is focused on gaining input through successive open comment periods and editing iterations of the SP draft. This phase will include multiple iterations of comments of approximately 2 weeks in length, followed by a 2-3 week period for the editors to adjudicate comments and make appropriate updates to the document.

We'll continue iterations for as long as we have feedback that results in meaningful changes. We welcome you to come back every iteration to see what's new, or watch daily. While we'll be posting major iterations every few weeks, we'll also make updates mid-cycle. 

### The first release

The work represented here is considered a stable draft, reflective of what NIST has learned about industry innovation, new threats, and an evolving landscape of federal digital services.  We have heard and learned so much through [public comment periods](http://csrc.nist.gov/groups/ST/eauthentication/sp800-63-2-comments-received-2015.pdf), [Executive Order 13681 -- Improving the Security of Consumer Financial Transactions](https://www.whitehouse.gov/the-press-office/2014/10/17/executive-order-improving-security-consumer-financial-transactions), [public workshops](http://csrc.nist.gov/publications/drafts/nistir-8103/nistir_8103_draft.pdf), and feedback from NIST's ongoing work such as NSTIC pilots and NCCoE industry collaborations.

But this release is neither complete nor perfect--and it's not intended to be. Rather, we believe we're at a point where we've articulated the direction we're going, but need our stakeholders to comment on what we got right, what we got wrong, and what we missed all together. We know that while SP 800-63 is scoped to federal agencies only, it has material impact on our private sector partners.  So we want to put fingers to keyboard with the community earlier and more often in hopes this update to SP 800-63 not only reflects the current state of the market, but has a level of future-proofing for where DIGITAL authentication to government services is going.  (Apologies to those that loved the term e-Authentication, but it's 2016, folks!)

## A quick summary

Here's a quick list for the biggest changes we've made, but you'll need to dig into the documents (yes, _documentS_) too:

1. LOA is decoupled into its component parts
2. Complete revamp of identity proofing
3. New password guidance
4. Removal of insecure authenticators (aka tokens)
5. Federation requirements and recommendations
6. Broader applicability of biometrics
7. Privacy requirements (under construction)
8. Usability considerations (under construction)
9. And many more...

Please note that the privacy and usability chapters are under construction.  We wanted to establish a baseline set of requirements before we plunged into those sections.  Expect to see content there in the future iterations, and we welcome suggestions!

## Why GitHub

Ok, "Why GitHub?" you ask. For us, the choice was relatively straightforward. GitHub has been a mainstay of the development and standards communities for many years now, serving as a space for collaborative interaction, the epicenter for evolving open source software, and an essential component in every coder’s toolkit. It only seemed appropriate for us to engage where so much of our community already congregates and collaborates. 

Second, as a platform, GitHub has many unique characteristics that make it attractive as a place to develop this special publication. From its ability to support broad engagement, to excellent version control, and multiple avenues for collecting and receiving input—it is a robust forum suited to this phase of drafting the 800-63-3 suite.

Overall, GitHub is the right tool for the job. But this is a new process for us; we don't want to leave anyone out, and we anticipate some growing pains as we work this out together. 

To that end, our use of GitHub is additive to the existing open and transparent process that NIST already follows. If you don't have the time this spring and summer to keep up with us, don't worry.  We will maintain our tradition of extended public comment after this process comes to a close.  

However, to manage this phase properly, we sincerely request that commenters provide substantive input.  Editorial or general comments will be accepted begrudgingly.  We want substantive technical/procedural comments.  We'll get to the grammar and formatting later. Trust us, this is as hard for some of the rather strict grammarians here at NIST as it is for anyone!

In addition, commenters are **STRONGLY** encouraged to collaborate with the team and other public participants via GitHub issues. See [this page](comment_help.html) for details on how to submit a comment to us.  We want to maintain a lean approach, so we are discouraging email and Excel files during this phase. We thank you in advance for your efforts to keep this process streamlined for the editors.

So have at it!  We're really excited about the changes we've made - we think you will be too!

Source information, current standards, and public comments received through May 2015 can be found [here](http://csrc.nist.gov/groups/ST/eauthentication/sp800-63-2_call-comments.html).

{% comment %}
<div class="text-center">
    <a href="sp800-63-3" class="btn btn-primary btn-lg" role="button">SP 800-63-3</a>
    <a href="sp800-63a" class="btn btn-primary btn-lg" role="button">SP 800-63A</a>
    <a href="sp800-63b" class="btn btn-primary btn-lg" role="button">SP 800-63B</a>
    <a href="sp800-63c" class="btn btn-primary btn-lg" role="button">SP 800-63C</a>
</div>
{% endcomment %}

<ul class="audiences">
<li>
  <div>
    <a href="sp800-63-3.html"><img src="assets/800_63_3_doc.png" alt="SP 800-63-3" width="150px" height="150px"></a>
  </div>
  <h3><a href="sp800-63-3.html">SP 800-63-3</a></h3>
  <h6>Digital Authentication Guideline</h6>
</li>
<li>
  <div>
    <a href="sp800-63a.html"><img src="assets/800_63_3_Proofing.png" alt="SP 800-63A" width="150px" height="150px"></a>
  </div>
  <h3><a href="sp800-63a.html">SP 800-63A</a></h3>
  <h6>Enrollment & Identity Proofing</h6>
</li>
<li>
  <div>
    <a href="sp800-63b.html"><img src="assets/800_63_3_Authenticators.png" alt="SP 800-63B" width="150px" height="150px"></a>
  </div>
  <h3><a href="sp800-63b.html">SP 800-63B</a></h3>
  <h6>Authentication & Lifecycle Management</h6>
</li>
<li>
  <div>
    <a href="sp800-63c.html"><img src="assets/800_63_3_Federation.png" alt="SP 800-63C" width="150px" height="150px"></a>
  </div>
  <h3><a href="sp800-63c.html">SP 800-63C</a></h3>
  <h6>Federation & Assertions</h6>
</li>
</ul>

</div>
</div>
</section>
