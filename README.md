# Poesy

## Poetic processing, for Python ##

Code developed in the Stanford Literary Lab's "Transhistorical Poetry Project" by Ryan Heuser (@quadrismegistus), J.D. Porter, Jonathan Sensenbaugh, Justin Tackett, Mark Algee-Hewitt, and Maria Kraxenberger. Cleaned and modified from [its original form](http://github.com/quadrismegistus/litlab-poetry) in 2018.

Poesy is built on [Prosodic](http://github.com/quadrismegistus/prosodic), a metrical-phonological parser written in Python.

### Create a poem: `poem = Poem()`

```python
from poesy import Poem

# create a Poem object by string
poem = Poem("""
When in the chronicle of wasted time
I see descriptions of the fairest wights,
And beauty making beautiful old rhyme
In praise of ladies dead and lovely knights,
Then, in the blazon of sweet beauty's best,
Of hand, of foot, of lip, of eye, of brow,
I see their antique pen would have express'd
Even such a beauty as you master now.
So all their praises are but prophecies
Of this our time, all you prefiguring;
And, for they look'd but with divining eyes,
They had not skill enough your worth to sing:
For we, which now behold these present days,
Had eyes to wonder, but lack tongues to praise.
""")

# or create a Poem object by pointing to a text file
la_belle_dame = Poem(fn='poems/keats.la_belle_dame_sans_merci.txt')
```

### Summary of annotations: `poem.summary()`



      (#s,#l)  parse                                             rhyme      #feet    #syll    #parse
    ---------  ------------------------------------------------  -------  -------  -------  --------
         1.1   WHEN|in.the|CHRON|i|CLE*|of|WAST|ed|TIME          a              5       10         2
         1.2   i|SEE|de|SCRIP|tions|OF*|the|FAI|rest|WIGHTS      b              5       10         1
         1.3   and|BEAU|ty|MAK|ing|BEAU|ti|FUL*|old*|RHYME       a              5       10         3
         1.4   in|PRAISE|of|LAD|ies|DEAD|and|LOVE|ly|KNIGHTS     b              5       10         1
         1.5   THEN|in.the|BLA|zon|OF*|sweet*|BEAU|tys|BEST      c              5       10         8
         1.6   of|HAND|of|FOOT|of|LIP|of|EYE|of|BROW             d              5       10         1
         1.7   i|SEE|their.an*|TIQUE.PEN*|would|HAVE|ex|PRESSD   c              4       10         5
         1.8   EV|en|SUCH*|a|BEAU|ty|AS*|you|MAS|ter|NOW         d              6       11         1
         1.9   so|ALL|their|PRAIS|es|ARE*|but|PRO|phe|CIES*      e              5       10         3
         1.1   OF*|this.our|TIME|all|YOU*|pre|FIG|ur|ING*        f              5       10        15
         1.11  and.for|THEY.LOOKD*|but|WITH*|di|VIN|ing|EYES     e              4       10         3
         1.12  THEY|had.not|SKILL|en|OUGH|your|WORTH|to|SING     f              5       10         2
         1.13  for|WE|which|NOW|be|HOLD|these|PRE|sent|DAYS      e              5       10         1
         1.14  had|EYES|to|WON|der|BUT*|lack*|TONGUES|to|PRAISE  e              5       10         3


    estimated schema
    ----------
    meter: Iambic
    feet: Pentameter
    syllables: 10
    rhyme: Sonnet, Shakespearean (abab cdcd efefgg)

### All statistics: `poem.statd`

    {'beat_scheme': (5,),
     'beat_scheme_diff': 6,
     'beat_scheme_length': 1,
     'beat_scheme_repr': 'Pentameter',
     'beat_scheme_type': 'Invariable',
     'meter_ambiguity': 3.5,
     'meter_constraint_TOTAL': 0.14285714285714285,
     'meter_constraint_footmin-f-resolution': 0.022556390977443608,
     'meter_constraint_footmin-w-resolution': 0.0,
     'meter_constraint_strength_w=>-p': 0.0,
     'meter_constraint_stress_s=>-u': 0.09774436090225563,
     'meter_constraint_stress_w=>-p': 0.022556390977443608,
     'meter_length_avg_line': 10.071428571428571,
     'meter_length_avg_parse': 10.071428571428571,
     'meter_mpos_s': 0.5037593984962406,
     'meter_mpos_ss': 0.015037593984962405,
     'meter_mpos_w': 0.43609022556390975,
     'meter_mpos_ww': 0.045112781954887216,
     'meter_perc_lines_ending_s': 1.0,
     'meter_perc_lines_fourthpos_s': 0.8571428571428571,
     'meter_perc_lines_fourthpos_w': 0.14285714285714285,
     'meter_perc_lines_starting_s': 0.35714285714285715,
     'meter_perc_lines_starting_w': 0.6428571428571429,
     'meter_type_foot': 'binary',
     'meter_type_head': 'final',
     'meter_type_scheme': 'iambic',
     'num_lines': 14,
     'rhyme_scheme': ('Sonnet, Shakespearean', 'abab cdcd efefgg'),
     'rhyme_scheme_accuracy': 0.6363636363636364,
     'rhyme_scheme_form': 'abab cdcd efefgg',
     'rhyme_scheme_name': 'Sonnet, Shakespearean',
     'rhyme_schemes': [(('Quatrain And Triplet', 'ababccc'), 0.4),
      (('Sonnet C', 'ababacdc edefef'), 0.4),
      (('Sonnet E', 'abab cbcd cdedee'), 0.4117647058823529),
      (('Sonnet A', 'abab cdcd eefeff'), 0.6153846153846154),
      (('Sonnet, Shakespearean', 'abab cdcd efefgg'), 0.6363636363636364)],
     'syll_scheme': (10,),
     'syll_scheme_diff': 1,
     'syll_scheme_length': 1,
     'syll_scheme_repr': 10,
     'syll_scheme_type': 'Invariable'}


## Installing

### 1. Poesy

Install from pip (preferred):

```
pip install poesy
```

Or install latest sources (advanced):

```
git clone git@github.com:quadrismegistus/poesy.git
cd poesy
python setup.py develop
```

### 2. (optional) eSpeak

[eSpeak](http://espeak.sourceforge.net/) is an open-source TTS engine for Windows and Unix systems (including Mac OS X). Poesy, built on [Prosodic](https://github.com/quadrismegistus/prosodic), uses it in order to sound out unfamiliar words.

[Download eSpeak for your operating system](http://espeak.sourceforge.net/download.html). Or, if you're running Mac OS X, install eSpeak with the [HomeBrew package manager](http://brew.sh/):

```brew install espeak```
