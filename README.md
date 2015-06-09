# Wikipedia Word Sense Induction and Disambiguation Task

## Introduction
This is a *word sense induction (WSI) and disambiguation (WSD)* dataset I extracted from Wikipedia using its link structure.

For this I used internal links within Wikipedia ("wiki links"):
Given a link like `[[Bank (Geography)|bank]]`, "Bank (Geography)", i.e. the link target,
is considered a word sense of "bank", i.e. the visible link text. By collecting all links using "bank" as link text, it is possible to gather many
senses of the word "bank", and of many other words.

To filter out link targets that do not represent real word senses, I kept only targets that occured in at least 10% of the cases for a given link text,
and did some manual filtering on top of that.

## Files
words-dev: 100 words provided as the "dev" (development) set
words-dev-withtargets: the same words with targets (see below for explanation)
instances-dev-100perword-lemmas-deps: 100 instances for each dev word
words-test: 100 words provided as the "test" set
words-test-withtargets: the same words with targets
instances-test-100perword-lemmas-deps: 100 instances for each test word

## File Structure
Both *-withtargets files contain rows with 4 columns. The first column is the word itself, the second colum the number of times this word was seen as
link text, the third column the number of discovered senses, and the fourth column the discovered senses, each with a observed frequency. If the
frequencies of the senses do not sum up to the frequency of the word, then this is due to link targets that were dropped in the filtering process
mentioned above. Here's an exemplary line:

`stress  5345    3       Stress_(mechanics):2092  Stress_(biology):1788  Stress_(linguistics):727`

Here's an exemplary line of the instances-* files:

`stress  Stress_(mechanics)      other application may be in medical sonography and elastography measure the stress or pressure level in relevant elastic tissue type ( e .g .   det(@@,the) dobj(measure,@@) cc(@@,or) conj(@@,level)`

As you can see, the file again contains 4 columns. The first column is the word itself, the second the appropriate sense (as linked in this context), the third column is the set ("bag") of lemmas in this context, and the fourth column the collapsed Stanford dependencies of the context.
