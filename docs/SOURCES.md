# Sources and verification status

Links come from search results gathered while preparing the talk; open each one before citing. Access to the *Science* and *Nature* pages may be restricted.

## Primary sources

1. **Ginsberg, Mohebbi, Patel, Brammer, Smolinski, Brilliant (2009).** *Detecting influenza epidemics using search engine query data.* Nature 457, 1012–1014. doi:10.1038/nature07634
   - Google-hosted copy: https://research.google.com/archive/papers/detecting-influenza-epidemics.pdf
   - Bias to state: written by the designers of GFT (most authors at Google, one at the CDC), so it evaluates their own tool.
2. **Lazer, Kennedy, King, Vespignani (2014).** *The Parable of Google Flu: Traps in Big Data Analysis.* Science 343(6176), 1203–1205. doi:10.1126/science.1248506
   - Publisher page: https://science.sciencemag.org/content/343/6176/1203
   - Bias to state: an external critique, but the authors could not recover the 45 queries, so their explanations are described as *probable*, not proven.
3. **Butler (2013).** *When Google got flu wrong.* Nature 494, 155–156. doi:10.1038/494155a
   - https://www.nature.com/articles/494155a (full text may be restricted)

## Secondary sources (context only, not for citing figures)

- University of Houston press release via ScienceDaily (13 March 2014): https://www.sciencedaily.com/releases/2014/03/140313142608.htm
- Wikipedia, *Google Flu Trends*: https://en.wikipedia.org/wiki/Google_Flu_Trends

## Verification status of the figures used

**Read in the main text of Lazer et al. (2014):**
- ~50 million candidate search terms fitted to 1,152 data points.
- Nature reported in February 2013 that GFT predicted more than double the CDC's proportion of influenza-like-illness doctor visits.
- Out-of-sample MAE in the main-text figure caption: 0.486 (GFT alone), 0.311 (lagged CDC), 0.232 (GFT + lagged CDC).
- Search-engine changes dated June 2011 (related searches) and February 2012 (potential diagnoses for symptom searches).
- The authors describe GFT as partly a "winter detector" and report that the developers themselves removed seasonal terms such as high-school basketball.

**Not re-checked against the originals; verify before presenting or citing:**
- From Ginsberg et al. (2009): 0.90 correlation on the fitting period, 0.97 on 42 validation weeks, ~450 million models, Fisher transformation, 4-fold cross-validation, "high school basketball" appearing in the top 100.
- From the Lazer et al. *supplement*: the 0.486 / 0.412 / 0.303 figures with a 3-week lag (slide 6 shows 0.303 and "−38%", while the main-text caption reports 0.232 for a different configuration: make sure the slide label matches the supplement), the neural-network MAE range 0.236–0.249, and the dates for drug information cards (Nov. 2012) and geolocation (July 2011).
- The 2015 shutdown of public GFT estimates: taken from secondary sources. The speaker note for slide 3 attributes it in part to Butler (2013), which was published before the shutdown; cite a source dated 2015 or later instead.
- Any study mentioned on Wikipedia: find and read the original before citing it.
