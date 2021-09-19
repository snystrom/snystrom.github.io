+++
title = "Purifying monoclonal antibodies (for CUT&RUN or other reasons)"
date=2021-09-19

slug = "Monoclonal antibody purification"

[extra.author]
name = "Spencer"

[taxonomies]
categories = ["Protocols"]
tags = ["cut&run"]
+++

I spent years of my PhD sequencing mouse instead of *Drosophila* DNA. Now you don't have to!

Fun fact: if you use monoclonal antibodies from the [Developmental Studies
Hybridoma Bank (DSHB)](https://dshb.biology.uiowa.edu/), they're full of mouse
nuclei & genomic DNA. This has a nasty consequence for low-input assays such as
[CUT&RUN](https://elifesciences.org/articles/21856), since the mouse DNA will
swamp out real signal. This issue is multiplied when using a model organism
with a smaller genome size than mouse (like *Drosophila*), because outcompeting
the contaminating DNA becomes almost impossible when using a smaller genome.

This issue isn't present during ChIP-seq because typically, antibodies are
first bound to magnetic beads, which are washed & purified away from the dirty
supernatant before IP-ing chromatin on the beads. This approach doesn't work
for CUT&RUN because it's *in-situ*, the antibody must be added in solution to
the tissue. Hence, we need a different way to purify the antibody before the
digest that retains activity while removing contaminating DNA. Of course,
there are other reasons you may not want DNA or nuclei in your antibody, this
protocol should work for those, too. 

## Is my antibody contaminated?

Great question. Here are a few easy ways to check:

1. Quantify nucleic acid concentration of your raw antibody using a Qubit. 
	- I like the high-sensitivity dsDNA Qubit kit for this since it is very specific for DNA
2. DAPI stain a small volume of antibody & mount on a hemocytometer
	- If your sample is anything like mine, it will look like the night sky, full of in-tact and blebbing mouse nuclei

You can repeat these steps after purification, and if it worked you should read 0ng/uL of DNA, and see 0 nuclei. Yes it's that clean.

## How do I fix it?

After trying a lot of things that didn't work, Kami Ahmad suggested I try using
magentic proteinG beads to purify the antibody away from the nuclei/DNA crap.
It worked great. 

The protocol works as follows:

1. Bind the antibody to magnetic beads
2. Wash away the supernatant contaminated with nuclei & DNA
3. Elute the antibody from the beads using an acidic pH (2.5 for proteinG beads, ~3.0-3.3 for proteinA beads)
4. Quickly neutralizing the acidic elution buffer to prevent denaturing the antibody

Honestly the hardest part is making the buffers, and they're really easy to make.

### Some thoughts

I let the antibody incubate for 40 minutes on beads, even though the thermo
manual for dynabeads says you can do it in 10. This was mostly because I had an
older set of beads and I was so tired of things not working by this point in
grad school that I didn't mind waiting an extra 1/2 hour. 

I do 2 rounds of elution to maximize recovery of antibody & to cut down on the
time the antibody sits in elution buffer. I always pooled the 2 eluates and
never tested whether the second one was high yield. 

Another great test after purification is to perform immunofluorescence using
the purified and unpurified antibodies in parallel. If the purification worked
correctly, you should observe similar intensity staining using pre- vs
post-purification antibody. To correctly account for the difference in antibody
volumes, treat the purified antibody as a dilution of the stock. For exmple, if
you input 12uL unpurified antibody, after purification you are left with 120uL of purified antibody. That's a 1:10 dilution.
So if in a normal immunofluorescence experiment you would use a 1:100 dilution
of stock antibody, you would use a 1:10 dilution of the purified antibody. Use
this same approach when determining the concentration of purified antibody to
use for CUT&RUN.

I use a Tris-Glycine elution strategy, but there are other [gentle antibody
elution
buffers](https://www.thermofisher.com/order/catalog/product/21027#/21027) which
may be better for certain antibodies. If you use these, you also have to use an
ion exchange column (like a [Zeba
column](https://www.thermofisher.com/us/en/home/life-science/protein-biology/protein-purification-isolation/protein-dialysis-desalting-concentration/zeba-desalting-products/zeba-spin-desalting-columns.html)
to swap the buffers because they're full of chaotropic agents (I think, I dunno
what's in them, although I tried to find out... see references). This protocol
is so easy to do, I'd try the Tris-Glycine approach first, then if the antibody
loses activity in immunofluorescence, you can try a different buffer. But first
make sure you're not letting the elution sit too long! Try shortening the
elution time and see if that helps first.

Good luck!

<h2>
<a href="/protocol_pdfs/mouse_antibody_purification_using_pGDynabeads_v1.pdf" target="_blank">
<span class="icon-text">
	<span class="icon">
		<i class="fas fa-download"></i>
	</span>
	&nbsp;&nbsp;Protocol download here
</span>
</a>
</h2>



<br>
</br>

### References:


* [NEB Antibody Purification w/ pAG beads](https://www.neb.com/protocols/0001/01/01/purification-of-igg-using-protein-ag-magnetic-beads)

* [CSH Phosphate Buffer Recipe](http://cshprotocols.cshlp.org/content/2006/1/pdb.rec8303.full)

* [protein G manual](https://www.bio-rad-antibodies.com/static/2015/proteus/protein-g-handbook.pdf)
  - BioRad protein G purification manual (This one is GREAT)

* [Pierce Gentle ab elution buffer](https://www.thermofisher.com/order/catalog/product/21027#/21027)

* [Sigma gentle pAG buffers](https://assets.thermofisher.com/TFS-Assets/LSG/manuals/MAN0011176_Gentle_AgAb_Bind_Elution_Buff_UG.pdf)
 - Thought: using phosphate-free system could be better because of CUT&RUN in addition to being better for abs
   - Note: This wasn't an issue for me, but could be in some cases.

* [DSHB Product Forms](https://dshb.biology.uiowa.edu/product-forms)
  - Antibodies are delivered in PBS
  - concentrate is supernatant run through 100kda size exclusion filter

* [Paper on MNase inhibitors/biochemistry](https://www.jbc.org/content/243/3/651.full.pdf)
 	- dNdp's inhibit MNase activity (dA/Tp in particular)
  	- ie di-phosphate nucleotides w/ 3' P.

* [G biosci gentle elution buffer](https://www.gbiosciences.com/image/pdfs/protocol/Gentle_Elution_Buffers.pdf)
  - use Tris/HEPES/MOPS ph 7.2-7.4 buffer w/ 150mM salt (no phosphates)
  - Neutralization Buffer: 1M Tris, pH8.0

* Sadly, I dug up an amazing set of 2 comprehensive proteinA and proteinG antibody purification manuals from thermofisher (or maybe pierce) that were of extreme help that I can no longer dig up. They were like 40 pages each with detailed troubleshooting & biochemistry sections. If anyone finds something like this, please reach out. I asked thermo and they couldn't find them either. Maybe I'm crazy.

