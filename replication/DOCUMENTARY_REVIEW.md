# Documentary review and event-sample provenance

This note records the sample hierarchy used by the current manuscript. It supersedes older development notes that described the September 25 25-event specification as the preferred sample.

## Revision universe and mechanical screen

Using the pinned Paper 1 observed-document sequence and the threshold `|ΔPCSI| > 0.03`, the linked universe contains **127 revisions at 78 institutions: 47 upward and 80 downward**.

A mechanical screen removes candidate events when the same institution has another threshold revision inside the target event window or when the linked AUTM panel lacks usable core-outcome support. **62 revisions** pass this screen. The screen is defined without consulting estimated technology-transfer effects.

## Documentary review

Twenty-five mechanically eligible events had been hand reviewed in the September 25 specification. The remaining **37 mechanically eligible pairs** were subsequently reviewed using the same documentary criteria:

- Comparability `C`: same governing IP/patent policy.
- Comparability `P`: partially comparable, such as excerpt/full-policy or campus/governing-board versions with overlapping IP governance.
- Comparability `N`: not a matched governing-policy pair.
- Timing `A`: documented adoption/revision date with no documented intervening version, or documents no more than two years apart.
- Timing `B`: documented adoption/effective/revision date but incomplete predecessor revision history.
- Timing `C`: intervening versions are documented or no usable revision date can be established.

A pair is usable when comparability is `C` or `P` and timing is `A` or `B`.

Of the 37 second-pass pairs, **nine** pass the documentary rule: **2 upward and 7 downward**. The complete row-level decisions and source-based rationales are in `data/revision_codes_rereview37.csv`.

## Current empirical hierarchy

1. **Preferred documentary sample:** 34 revisions at 32 institutions, **8 upward / 26 downward**. It combines the frozen 25-event benchmark with the nine second-pass additions.
2. **Strict post-support sensitivity:** 29 revisions, **7 upward / 22 downward**, after uniformly requiring at least two treated-institution core-outcome panel years in event times 0 through +5.
3. **Frozen September 25 benchmark:** 25 revisions, **6 upward / 19 downward**, retained for provenance and robustness.

The broader historical rule-coded specification is not part of the preferred documentary hierarchy.

## Pre-submission safeguard

The **nine second-pass documentary classifications must receive independent human/coauthor verification without viewing outcome estimates before journal submission**. Automated reproducibility checks verify that code consumes the recorded labels consistently; they cannot establish that the documentary judgments are substantively correct.

## Interpretation

The expanded review strengthens transparency of sample construction but does not make revision direction exogenous. Upward and downward revisions are chosen by universities, and the preferred sample has a large imbalance in predecessor-policy PCSI. The paper therefore treats the stacked event study as observational and the direction-label permutation procedure as an inferential sensitivity under an exchangeability assumption, not as design-based randomization inference.
