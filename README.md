Open source software for geographic analysis in transport planning
================
2019-08-16

# Abstract

Tools for working with geographic data have long been used in transport
planning. Transport is an inherently geographic activity, involving
movement through space, along more or less complicated ways which,
considered together, form interrelated spatial networks. There is
therefore a strong case for geography being an *inbuilt* part of the
transport planner’s ‘tools of the trade’.
<!-- --- software for transport data analysis, modelling and visualisation --- -->
<!-- workflows in academic, public sector and private consultancy transport planning contexts still tend to separate vital geographic processing and map making stages from the rest of the analysis. -->
Yet a dichotomy between ‘geographic’ and ‘non-geographic’ components
persists, damaging transport planning in three main ways, by: (1)
reducing researcher effectiveness due to the time-consuming process of
‘context switching’; (2) inhibiting reproducibility, requiring
installation and management of geographic and non-geographic tools; and
(3) reducing the visibility of vital geographic components in transport
planning, with consequences for transport policy design. These premises
are described in the wider context of transport planning research and
the landscape of transport planning software that is used in practice,
which is dominated by proprietary products. The paper then shifts gear,
to focus on open source software as a solution to the issues with the
current non-integrated approach to transport modelling and geographic
analysis. Three emerging software ecosystems that enable geographic
analysis *to be embedded within* transport planning workflows are
reviewed in depth: the programming languages R and Python, and the
geographic information system QGIS. The review finds that each ecosystem
already provides numerous new ‘tools of the trade’ for transport
planners who need to integrate geographic data in their work, with wider
benefits for reproducibility, transparency and democratic
accountability.
<!--  transport planning experts and the public alike, -->
<!-- Ultimately, by highlighting cost effective and geographically targeted interventions, integrating geographic analysis in transport planning could lead to better decision making. -->
<!-- and support the global efforts to transition away from fossil fuels and towards a healthy, low carbon transport system. -->

### Notes/questions

This paper is work in progress and its focus has shifted over time. A
previous working title was “Integrating geographic analysis in transport
planning: new open source tools for the trade”. The need to integrate
geographic analysis in transport planning is still a central theme of
the paper but the focus is now on solutions, in the form of open source
software. Does the paper now have too much on the importance on
integrating geographic analyis in transport planning, given the new
emphasis? And are there any other open source software projects I should
include, within or in addition to the overview of the three ecosystems
selected?

# Introduction: the importance of geographic analysis in transport planning

<!-- Should that heading omit the "Introduction:" part? -->

Transport planning is an applied discipline involving the design and
placement of physical infrastructure, including highways, railways,
cycleways and footways (O’Flaherty and Bell 1997; Parkin 2018). It also
involves visioning transport futures and making the economic and
political case for change (Timms, Tight, and Watling 2014). Successful
transport plans are therefore a combination of geographically specific
recommendations (e.g. “build this way here”) and long-term strategies
guided by citywide, regional and even national visions. The rewards can
be great: transport planners who have designed — and helped to implement
— plans appropriate to the needs of an area leave a legacy that will
benefit people and the environment for generations to come.\[1\]
Transport planning can be considered as “more of an art than a
technique”, although *good* transport plans also rely on robust
analysis and modelling of sometimes large and usually spatial input
datsets (Dios Ort’uzar and Willumsen 2001). Ways and other pieces of
transport infrastructure must *go somewhere* to optimise their ability
to take people *where they want to go*, yet the importance of geography
in transport systems is often overlooked (Rodrigue, Comtois, and Slack
2013). Transport planning is thus embedded within broader democratic
processes *and* local geographic contexts.

Effective transport planning is inherently embedded within democratic
processes (to the extent that democracy exists in the area where
transport plans are commissioned) because it determines how public
spaces and other shared resources are used, affecting everyone in
society. If transport plans are developed by unaccountable technocrats
with little understanding of their impacts, the results can be severe:
the transport system now is the “leading cause of death for children and
young adults aged 5-29 years” through road traffic casualties alone,
with 1.35 million people killed and tens of millions injured and
disabled each year (World Health Organization 2018). The air pollution
impacts could be even greater, with a growing body of research linking
air pollution to Alzheimer’s disease, lung cancer and heart disease
among hundreds of millions of sufferers worldwide (Kampa and Castanas
2008; Kilian and Kitazawa 2018). Transport is responsible for a quarter
of global greenhouse gas emissions and growing (Harrison and Hester
2017), and is one of the hardest sectors to decarbonise (Moriarty and
Honnery 2008), meaning that evidence-based plans to reduce transport
energy use is an urgent priority affecting the global population,
especially the projected 1.4 billion people who will live in low
elevation (less than 10 m above sea level) coastal zones by 2060
(Neumann et al. 2015).

Transport planning is also inherently embedded within local geographic
contexts because transport systems, and the networks of physical
infrastructure that underpins them, are highly localised (Barth’elemy
2011; Levinson 2012) and to some degree dynamic (Xie and Levinson 2011)
phenomena. Transport planning is therefore fundamentally a *spatial
activity*. Perhaps in response to an upsurge in the amount of geographic
transport data available, interest in Transport Geography seems to have
grown over the last decade relative to other terms, according to data
from Google Trends (Figure 1). It is interesting to compare this growth
with relative levels of interest in ‘geographic information systems’ and
‘spatial planning’, both of which seem to have seen relative declines
over time, notwithstanding the limitations associated with search data
(Mellon
2014).

<img src="google-trends.png" title="Relative level of interest in search terms related to 'geographic information systems', 'geocomputation' and 'transport geography' inferred from google search data. Thanks to the **gtrendsR** R package [@massicotte_gtrendsr:_2019], code to reproduce the plot is hosted in this paper's code repository." alt="Relative level of interest in search terms related to 'geographic information systems', 'geocomputation' and 'transport geography' inferred from google search data. Thanks to the **gtrendsR** R package [@massicotte_gtrendsr:_2019], code to reproduce the plot is hosted in this paper's code repository." width="70%" />

The concept of integrating geographic data analysis in transport
planning is not new (although tools for integrating geographic data
are). Geographic perspectives have contributed to the transport planning
for over 100 years, as documented in papers on geographic considerations
in railway design (Buxton 1908) and national engineering challenges
(Farnham 1912), to take just a couple of pre-war examples.

In the inter-war period (1918-1939), interest in Transport Geography
seems to have grown, although a disciplinary home for transport research
(let alone geographic transport research) had yet to emerge and the term
‘transport geography’ itself was vanishingly rare. A few papers from the
period demonstrate the growing interest in the topic, and understanding
of geographic thinking to understand evolving transport systems.
Paterson (1926) speculated quite accurately on the continued rise of
motor traffic at the expense of horse powered transport during the
20<sup>th</sup> Century, noting the importance of geographic factors in
determining mode choice, down to the street level: “Many streets, like
our Bond Street, Watling Street or Lombard Street, and in Seville, the
Calle de las Sierpes or Kalver Straat in Amsterdam, may be unsuited to
motor traffic, and frontage values may be so high that widening can
hardly be considered.” In a geographic review of Japanese cities
Trewartha (1934) also alluded to the relationship between geography and
mode choice: “widening and paving of \[roads\] have (sic) been
accomplished \[allowing\] numerous taxis, motor busses, and tram cars
contrasting with the slow human and animal-drawn carts and the
ubiquitous bicycle”. Rapid industrialisation during the largely
unconscious build-up to World War II was associated with major road
building schemes in many developed regions, demanding the practical
application of new methods from a range of disciplines (e.g.
Greenshields 1936). In the USA, highway engineering even became a
recommended case study for geography lessons (Fox 1923).

geographic

Around the turn of the century, there were attempts to define geographic
information systems for transportation (GIS-T) as a self-standing
academic field (Miller 1999), something that has not caught
on.

<!-- Search term for interwar period: https://scholar.google.co.uk/scholar?q="transport+geography" -->

<!-- something on the Journal of Transport Geography? -->

The growing research interest in the subject is also reflected in
teaching. Modules dedicated to Transport Geography have been advertised
at the Universities of Aberdeen and Hofstra and, at the University of
Leeds the Masters module Sustainable Spatial Planning and Analysis
([SSPA](https://github.com/ITSLeeds/SSPA)) is focussed on GIS skills for
transport planning (declaration of interest: I teach on this module).
There are even dedicated 3 year degrees Transport Geography.
<!-- something on the lack of open source? -->

<!-- https://www.abdn.ac.uk/registry/courses/undergraduate/2016-2017/geography/gg4016
https://people.hofstra.edu/jean-paul_rodrigue/course_transport.html
 in Geography with Transport Studies BA advertised by the University of Leeds
-->

Where is existing infrastructure and ‘demand’ (current and potential
travel) located? How will transport patterns shift in the future? And
where will different types of intervention be most effective? Tools that
can help answer these questions are becoming an increasingly important
part of the transport planner’s cabinet (te Brömmelstroet and Bertolini
2008).

To illustrate this point, imagine fundamental changes that could be made
to tax system in support a transition away from fossil fuels.
Interventions such as carbon taxes would undoubtedly have geographic
implications, but the intervention itself (charging a fixed price for
the extraction and sale of atmosphere polluting substances) could be
essentially non-geographic. Notwithstanding changes to national policies
relating to transport, transport planning interventions, by contrast,
are inherently spatial. Even high level national plans for a walking and
cycling revolution must be implemented locally, down to the level of
streets, as illustrated by the still ongoing local implementation of
Dutch cycling ambitions (Pucher and Buehler 2008). The
political-democratic and local-geographic aspects of transport planning
can be considered in isolation, but an integrated approach is necessary
for effective policies (Hull 2008). This is well illustrated by
prominent Mayoral transport policies in cities such as London\[2\],
Paris\[3\], and Bogotá\[4\].

With such issues — climate change, air pollution, obesity and social
inequalities — high on the political agenda, and the benefits for ‘early
adopters’ of evidence-based interventions to accelerate the shift away
from the motor car in cities such as London, Paris and Bogotá, pressure
is growing on local, city and national transport planning departments to
act. But what should they do? This *policy* question raises important
*research* questions: Which methods are most suitable for designing
future transport systems? What is the evidence base, and analysis, that
should be used to inform transition towards a healthy, zero carbon
transport system? Which interventions, from the multitude of options
available, are most likely to be effective? And where are different
types of intervention most likely to succeed? The premise of this paper
is that new approaches, enabled by software, are needed to provide
answers to these questions. 21<sup>st</sup> century demands for
transport planning cannot be delivered by 20<sup>th</sup> century
technology and, this paper will argue, open source solutions are poised
to bridge the gap between the geographic and the — historically dominant
— non-geographic aspects of transport planning. The 21<sup>st</sup>
Century also requires new transport planning methodologies which, as
this paper outlines, increasingly involves geographic analysis.
Furthermore, the policy context increasingly demands transparency and
citizen involvement in the decision-making process, which only software
that is open source and reliably deliver, making an exploration of open
source options for transport planning workflows timely.

Methods for transport planning are by no means static. They are
constantly evolving in response to policy drivers and technological
change (Boyce and Williams 2015). Of course, transport policies that are
evidence-based and grounded in realistic models of change under
different scenarios of the future are far more likely to be successful
than policies based on ideological commitment and good intentions alone.
With unprecedented access to increasingly detailed datasets on transport
behaviours and infrastructure, transport planners today can make their
designs are more evidence-based that ever, provided they have access to
tools that enable them to make sense of this ‘data revolution’
(Transport Systems Catapult 2015). The sheer volume and complexity of
new datasets require new approaches that can scale and integrate
multiple data sources (Lovelace et al. 2016). Furthermore, advances in
software and hardware allow not only for current transport systems to be
modelled at high temporal and geographic resolution, but for future
scenarios and ‘model experiments’ to be developed, which can support
identification and implementation of the most effective interventions
(Klosterman 1999). With the explosion in open source software, which has
come to dominate data science, there is now also a unique opportunity
for transport planning to become a more transparent and democratically
accountable enterprise.

Unfortunately, the dream of data driven, participatory and open
transport planning is far from reality. Transport planning has been slow
to adapt to the data revolution and, while it evolves to enable a wider
range of input data sources and analysis ‘in the cloud’, the open source
element is conspicuously lacking.

The paper outlines how the ‘division of labour’ between geographic and
non-geographic aspects of transport planning emerged, in relation to the
historical specialisation and monopolisation of particular transport
planning software products, based on existing literature and an
understanding of landscape of tools used in practice (Section 2).
Section 3 reviews open source software ecosystems that enable an
integrated approach, which combines non geographically explicit stages
(e.g. modelling) and geographic processing stages *in a single
workflow*. Three software ecosystems (R, Python and QGIS) are reviewed
in detail; alternative current and potential future approaches,
including ‘cloud lock in’ are discussed; and the relative merits of
different approaches are discussed. Building on this discussion, the
paper concludes by returning to the importance of integrating data
analysis and geographic processing in a single analysis. The final
section also outlines concrete steps that researchers, public sector
transport planners, and transport planning analysts and consultants can
take to accelerate the transition to open source software in transport
planning which will, in turn, support policies that accelerate the
transition to healthy and zero carbon transport
systems.

<!-- The paper concludes that 'integrated approach' can support efficient, scalable and reproducible transport planning workflows which can provide a strong and transparent evidence base needed for rapid transition away from fossil fuels in the transport sector. -->

# The landscape of transport planning software

Before describing the existing landscape, it is worth outline what
transport planning software is. Software for transport planning can be
grouped by the scale at which it operates, with broad categories being
‘micro’ and ‘macro’ models (Kotusevski and Hawick 2009). ‘Microscopic’
transport models represent individual vehicles on the road network and
are therefore able to represent localised phenomena such as traffic
congestion. Macro models, by contrast, represent aggregates of vehicular
traffic over large spatial scales, with a focus on the implications of
future changes in transport behaviour and infrastructure on flow at the
route network level. Of course the distinction is, in reality, an
oversimplification: there is a continuum between micro and macro
transport modelling software. With advances in computer hardware and
software, an increasing number of developers are attempting to combine
both approaches into a single system. In this paper we focus on macro
models, and their geographic representation, rather than micro models.

The geographic and non-geographic division of labour is a result of the
history of transport planning software. This history is detailed in
Chapter 10 of *Forecasting Urban Travel* (Boyce and Williams 2015).
Titled “Computing environment and travel forecasting software”, the
chapter provides a unique insight into the software packages that have
been popular in transport planning over the years. Of course, software
development has always depended on the physical hardware on which it
runs and the early days of transport planning software were
characterised by bespoke programs running on mainframe computers and
maintained by domain experts. Transport planning bodies and researchers
in the USA led developments in the 1960s and 1970s when computers first
started to be used for transport planning, when the main problem that
they addressed was how to deal with the explosive growth in car
ownership and use that was taking place during those decades. More
overtly political factors also influenced the direction of transport
planning software: “certain private firms complained to US DoT
\[Department of Transport\] that its agencies were developing software
in competition with the private sector”, leading to the abandonment of
publicly funded transport planning software development projects,
notably UTPS.\[5\] This contrasts with the history of GRASS, a publicly
funded GIS system that has been under continuous development by state,
academic and commercial organisation since 1982 (Neteler and Mitasova
2008). Would the landscape of transport planning software have been
different if the DoT had continued to fund software development
projects? That question is outside the scope of this paper. What is
certain, however, is that software used in transport planning over the
past three decades has been dominated by companies and that the sector
has been slow to adopt open an open source approach.

In response to the ‘siloed’ development of GIS and transport software,
there have been calls for greater integration. Loidl et al. (2016),
building on the observation that “geography and GIS remained a niche
topic within traditional transport modeling”, made a case for
strengthening the ‘spatial perspective’ in transport modelling. The
paper emphasised the growing importance of well-defined data types,
disaggregating detailed (and difficult to interpret) transport model
outputs, and geographic data visualisation and concluded that much
further research is needed: “future research and development is needed
to combine geospatial functionalities with transport modeling, while
providing an efficient, interactive, visual interface for data
exploration, manipulation, analysis and visualization” (Loidl et al.
2016). Although the paper focussed on conceptual issues rather than
software per-se, it did identify mention four open source programming
languages that could provide the foundation for future developments, two
of which (R and Python) are covered in the next section.

Data preprocessing and analysis stages are generally done in dedicated
transport planning and spreadsheet software. Geographic analysis and
cartographic visualisation stages are generally done in a dedicated
‘geographic information system’ (GIS).

# New tools of the trade

The previous sections support and expand on the two main premises of
this paper: that geographic analysis has historically been disconnected
from other aspects of transport planning analysis, and that the
incumbent proprietary software products are not well suited to tackle
21<sup>st</sup> Century transport planning needs. In this section the
paper shifts gear, and moves onto solutions. It outlines the growth of
free and open source software (FOSS) and how the movement can provide
the foundations for more democratic and transparent transport planning
workflows that bridge the ‘geographic gap’ in transport planning data
analysis, modelling and visualisation. The focus is on three software
‘ecosystems’ — R, Python and QGIS — that are particularly promising
for integrated geographic analysis in transport planning.

Before exploring these ecosystems, it is worth first taking a step back
and considering the open source software ‘landscape’ and what ‘open
source’ actually means. This overview also helps explain why R, Python
and QGIS were selected from the range of open source options for closer
attention.

<!-- Despite the central role that open source software plays, powering the majority of the world's servers... -->

Open source software differs from proprietary software in that users are
free to see, download and modify the underlying source code that defines
it. Freedom is central to open source software, which is sometimes
referred to simply as ‘free software’, defined by the Free Software
Foundation ([FSF](https://www.fsf.org/about/what-is-free-software)) as
follows:

> software that gives you the user the freedom to share, study and
> modify it.

This adaptability is conducive to collaboration, the creation of
mutually supportive user/developer communities and rapid evolution,
making open source software ecosystems fast moving and highly diverse.
It is impossible to discuss all software options that could be used for
geographic transport planning: there are literally thousands of software
projects, written in hundreds of programming languages, many of which
are no longer actively maintained. Transport planners should use
solutions that are future proof and actively maintained — such as R,
Python and QGIS.

Transport data analysis has much in common with the broadly defined
field of ‘data science’, and many of the tools developed for this
purpose (including those in the R and Python ecosystems) have great
potential for transport planning.

  - Scala
  - JavaScript
  - …

## R

R is a “a language and environment for statistical computing and
graphics” (R Core Team 2019). First announced and released as a binary
program in 1993 by University of Aukland statisticians Robert Gentleman
and Ross Ihaka, the project was only open sourced and released under the
conditions of the GNU General Public License (GPL) in 1995, thanks to
input from one of R’s first international collaborators, Martin Mächler
of ETH Zurich (Ihaka 1998). This history highlight’s how open source
software development is an inherently collaborative process, usually
involving people from many different countries and backgrounds.

R has several strengths from the perspective of transport planning,
including its proficiency with temporal and geographic data, outstanding
visualisation capabilities, and support for a very wide range of
statistical techniques, many of which are useful in transport problems
(Lovelace and Ellison 2018). Out of the box R is a statistical powertool
that can solve a wide range of problems, including generalised linear
models (GLMs, implemented with the function `glm`) and constrained
optimisation problems that appear frequently in transport research.
Additional capabilities are supported by 10,000+ packages that can be
installed from a central repository with commands such as
`install.packages("stplanr")`.\[6\]

A good example of a transport problem that R’s statistical capabilities
are well suited to solving is mode choice. Unimodal models estimating
mode share (or the logit thereof) can use R’s inbuilt statistical
capabilities, as demonstrated in the Propensity to Cycle Tool project
(Lovelace et al. 2017). More sophisticated multinomial models are needed
when estimating mode share across multiple travel options such as walk,
cycle, bus (Mart’ın and P’aez 2019). R has mature support for such
models via the `multinom` function in the longstanding package `nnet`
(Venables and Ripley 2002), as demonstrated by [Germán
Rodríguez](https://data.princeton.edu/wws509/r/c6s2). Subsequent
packages provide additional methods for estimating mode split (Hasan,
Wang, and Mahani 2016; Croissant 2019), and packages such as `appollo`
and `mlr3` provide support for sophisticated choice models and machine
learning
(<span class="citeproc-not-found" data-reference-id="xxx">**???**</span>).

R is well known for having outstanding statistical analysis and
modelling capabilities, of the type useful in transport planning. Less
known is that R also has a mature ecosystem for working with geographic
data, making it well suited to the task of integrating geographic
analysis in transport planning: R excels at doing modelling *and*
geographic analysis. This is particular interest here because, as
outlined in previous sections, ‘context switching’ between programs for
statistical and geographic analysis is time consuming.\[7\] Support for
geographic data and methods have a long history in R (Rowlingson et al.
2003; Bivand 2006; Pebesma et al. 2015; Bivand, Pebesma, and
G’omez-Rubio 2013). The development of R’s spatial capabilities are
well documented elsewhere \[link to other articles in the special
edition\]. However, a few advances are worth mentioning due to their
relevance to transport transport planning. The package `sf` (Pebesma
2018) provides a unified and high performance system for working
geographic lines (in addition to its support for points and polygons),
which can be used to represent roads. Building on `sf`, the package
`stplanr` (Lovelace and Ellison 2018) provides many functions for
working with geographic transport data, including `overline` which
enables thousands routes to be aggregrated to create route networks
(Morgan and Lovelace, in press) and `dl_stats19`, which has evolved into
the `stats19` package (Lovelace et al. 2019). Geographic data
visualisation, cartography, is another area where R excels, with
packages such as `tmap` (Tennekes 2018) providing powerful functions for
map making. These and many other packages for working with geographic
data in R are described in detail in *Geocomputation with R* (Lovelace,
Nowosad, and Meunchow 2019). Chapter 12 this of this open source book is
dedicated to transport applications, and provides a good starting point
for learning more about using R’s impressive geographic capabilities for
transport planning.

## Python

Python is a general-purpose programming language originally conceived in
the late 1980s and first released in 1991 (Rossum 1995). The language
was designed from a computer science perspective, with a focus on code
elegance and consistency, rather than R’s focus on statistical
functionality. However, Python has become very popular for data analysis
and ‘data science’ thanks to packages such as
[Pandas](https://github.com/pandas-dev/pandas), and SciKitLearn
(McKinney 2017). more on computer science, with than statist

(Zandbergen 2015)

Many Python packages have been developed for transport applications.
(Boeing 2017).

A recent and ambitious project
(<span class="citeproc-not-found" data-reference-id="pappalardo_scikit-mobility_2019">**???**</span>)

Like R, Python has interfaces to many other languages.

Because Python is a general purpose language, it has been used as the
basis of transport applications that go beyond the transport planning
remit of this paper. A couple of projects are worth mentioning to give
an indication of the wider Python transport ecosystem.
[Itinerum](https://github.com/TRIP-Lab) is an open source travel survey
development project, which includes a backend written in Python and
smartphone apps
(<span class="citeproc-not-found" data-reference-id="patterson_itinerum_2019">**???**</span>).
A similar project is [E-mission](https://github.com/e-mission) (Shankari
et al. 2018) the backend of which is partly written in Python.

## QGIS

(QGIS Development Team 2019)

# Conclusion

# References

<div id="refs" class="references">

<div id="ref-barthelemy_spatial_2011">

Barth’elemy, Marc. 2011. “Spatial Networks.” *Physics Reports* 499
(1–3): 1–101.

</div>

<div id="ref-bivand_implementing_2006">

Bivand, Roger. 2006. “Implementing Spatial Data Analysis Software Tools
in R.” *Geographical Analysis* 38 (1): 23–40.
<https://doi.org/10.1111/j.0016-7363.2005.00672.x>.

</div>

<div id="ref-bivand_applied_2013">

Bivand, Roger, Edzer J Pebesma, and Virgilio G’omez-Rubio. 2013.
*Applied Spatial Data Analysis with R*. Vol. 747248717. Springer.

</div>

<div id="ref-boeing_osmnx:_2017">

Boeing, Geoff. 2017. “OSMnx: New Methods for Acquiring, Constructing,
Analyzing, and Visualizing Complex Street Networks.” *Computers,
Environment and Urban Systems* 65 (September): 126–39.
<https://doi.org/10.1016/j.compenvurbsys.2017.05.004>.

</div>

<div id="ref-boyce_forecasting_2015">

Boyce, David E., and Huw C. W. L. Williams. 2015. *Forecasting Urban
Travel: Past, Present and Future*. Edward Elgar Publishing.

</div>

<div id="ref-buxton_balkan_1908">

Buxton, Noel. 1908. “Balkan Geography and Balkan Railways.” *The
Geographical Journal* 32 (3): 217–34.

</div>

<div id="ref-croissant_mlogit:_2019">

Croissant, Yves. 2019. *Mlogit: Multinomial Logit Models*.
<https://CRAN.R-project.org/package=mlogit>.

</div>

<div id="ref-ortuzar_modelling_2001">

Dios Ort’uzar, Juan de, and Luis G. Willumsen. 2001. *Modelling
Transport*. John Wiley; Sons.

</div>

<div id="ref-farnham_relation_1912">

Farnham, Amos W. 1912. “The Relation of Some Recent Engineering Problems
to Geography.” *Journal of Geography* 11 (2): 40–45.

</div>

<div id="ref-fox_main_1923">

Fox, Florence C. 1923. *Main Streets of the Nation a Series of Projects
on Highway Transport for Elementary Schools*. Department for the
Interior.

</div>

<div id="ref-greenshields_studying_1936">

Greenshields, Bruce D. 1936. “Studying Traffic Capacity by New Methods.”
*J. Appl. Psychol* 20 (3): 353–58.

</div>

<div id="ref-harrison_environmental_2017">

Harrison, R. M., and R. E. Hester. 2017. *Environmental Impacts of Road
Vehicles: Past, Present and Future*. Royal Society of Chemistry.

</div>

<div id="ref-hasan_fast_2016">

Hasan, Asad, Zhiyu Wang, and Alireza S. Mahani. 2016. “Fast Estimation
of Multinomial Logit Models: R Package Mnlogit.” *Journal of Statistical
Software* 75 (1): 1–24. <https://doi.org/10.18637/jss.v075.i03>.

</div>

<div id="ref-hull_policy_2008">

Hull, Angela. 2008. “Policy Integration: What Will It Take to Achieve
More Sustainable Transport Solutions in Cities?” *Transport Policy*, New
Developments in Urban Transportation Planning, 15 (2): 94–103.
<https://doi.org/10.1016/j.tranpol.2007.10.004>.

</div>

<div id="ref-ihaka_r:_1998">

Ihaka, Ross. 1998. “R: Past and Future History.” *Computing Science and
Statistics* 392396.

</div>

<div id="ref-kampa_human_2008">

Kampa, Marilena, and Elias Castanas. 2008. “Human Health Effects of Air
Pollution.” *Environmental Pollution*, Proceedings of the 4th
International Workshop on Biomonitoring of Atmospheric Pollution (With
Emphasis on Trace Elements), 151 (2): 362–67.
<https://doi.org/10.1016/j.envpol.2007.06.012>.

</div>

<div id="ref-kilian_emerging_2018">

Kilian, Jason, and Masashi Kitazawa. 2018. “The Emerging Risk of
Exposure to Air Pollution on Cognitive Decline and Alzheimer’s
Disease–Evidence from Epidemiological and Animal Studies.” *Biomedical
Journal*.

</div>

<div id="ref-klosterman_what_1999">

Klosterman, R. E. 1999. “The What If? Collaborative Planning Support
System.” *Environment and Planning B: Planning and Design* 26 (3):
393–408. <https://doi.org/10.1068/b260393>.

</div>

<div id="ref-kotusevski_review_2009">

Kotusevski, G., and K. A. Hawick. 2009. “A Review of Traffic Simulation
Software.” *Research Letters in the Information and Mathematical
Sciences* 13: 35–54. <https://mro.massey.ac.nz/handle/10179/4506>.

</div>

<div id="ref-levinson_network_2012">

Levinson, David. 2012. “Network Structure and City Size.” *PloS One* 7
(1): e29721. <https://doi.org/10.1371/journal.pone.0029721>.

</div>

<div id="ref-loidl_gis_2016">

Loidl, Martin, Gudrun Wallentin, Rita Cyganski, Anita Graser, Johannes
Scholz, and Eva Haslauer. 2016. “GIS and Transport
Modeling—Strengthening the Spatial Perspective.” *ISPRS International
Journal of Geo-Information* 5 (6): 84.
<https://doi.org/10.3390/ijgi5060084>.

</div>

<div id="ref-lovelace_big_2016">

Lovelace, Robin, Mark Birkin, Philip Cross, and Martin Clarke. 2016.
“From Big Noise to Big Data: Toward the Verification of Large Data
Sets for Understanding Regional Retail Flows.” *Geographical Analysis*
48 (1): 59–81. <https://doi.org/10.1111/gean.12081>.

</div>

<div id="ref-lovelace_stplanr:_2018">

Lovelace, Robin, and Richard Ellison. 2018. “Stplanr: A Package for
Transport Planning.” *The R Journal* 10 (2): 7–23.
<https://doi.org/10.32614/RJ-2018-053>.

</div>

<div id="ref-lovelace_propensity_2017">

Lovelace, Robin, Anna Goodman, Rachel Aldred, Nikolai Berkoff, Ali
Abbas, and James Woodcock. 2017. “The Propensity to Cycle Tool: An Open
Source Online System for Sustainable Transport Planning.” *Journal of
Transport and Land Use* 10 (1). <https://doi.org/10.5198/jtlu.2016.862>.

</div>

<div id="ref-lovelace_stats19:_2019">

Lovelace, Robin, Malcolm Morgan, Layik Hama, and Mark Padgham. 2019.
“Stats19: A Package for Working with Open Road Crash Data.” *Journal
of Open Source Software*. <https://doi.org/10.21105/joss.01181>.

</div>

<div id="ref-lovelace_geocomputation_2019:1">

Lovelace, Robin, Jakub Nowosad, and Jannes Meunchow. 2019.
*Geocomputation with R*. CRC Press. <http://robinlovelace.net/geocompr>.

</div>

<div id="ref-martin_individual_2019">

Mart’ın, Bel’en, and Antonio P’aez. 2019. “Individual and Geographic
Variations in the Propensity to Travel by Active Modes in
Vitoria-Gasteiz, Spain.” *Journal of Transport Geography* 76: 103–13.

</div>

<div id="ref-mckinney_python_2017">

McKinney, Wes. 2017. *Python for Data Analysis: Data Wrangling with
Pandas, NumPy, and IPython*. 2 edition. Sebastopol, California: O’Reilly
Media.

</div>

<div id="ref-mellon_internet_2014">

Mellon, Jonathan. 2014. “Internet Search Data and Issue Salience: The
Properties of Google Trends as a Measure of Issue Salience.” *Journal of
Elections, Public Opinion and Parties* 24 (1): 45–72.
<https://doi.org/10.1080/17457289.2013.846346>.

</div>

<div id="ref-miller_potential_1999">

Miller, Harvey J. 1999. “Potential Contributions of Spatial Analysis to
Geographic Information Systems for Transportation (GIS-T).”
*Geographical Analysis* 31 (4): 373–99.
<https://doi.org/10.1111/j.1538-4632.1999.tb00991.x>.

</div>

<div id="ref-moriarty_prospects_2008">

Moriarty, Patrick, and Damon Honnery. 2008. “The Prospects for Global
Green Car Mobility.” *Journal of Cleaner Production* 16 (16): 1717–26.
<https://doi.org/10.1016/j.jclepro.2007.10.025>.

</div>

<div id="ref-neteler_open_2008">

Neteler, Markus, and Helena Mitasova. 2008. *Open Source GIS: A GRASS
GIS Approach*. Third. New York, NY: Springer.

</div>

<div id="ref-neumann_future_2015">

Neumann, Barbara, Athanasios T. Vafeidis, Juliane Zimmermann, and Robert
J. Nicholls. 2015. “Future Coastal Population Growth and Exposure to
Sea-Level Rise and Coastal Flooding-a Global Assessment.” *PloS One* 10
(3): e0118571.

</div>

<div id="ref-oflaherty_transport_1997">

O’Flaherty, Coleman, and Michael GH Bell. 1997. *Transport Planning and
Traffic Engineering*. Elsevier.

</div>

<div id="ref-parkin_designing_2018">

Parkin, John. 2018. *Designing for Cycle Traffic: International
Principles and Practice*. ICE Publishing.
<https://www.icevirtuallibrary.com/isbn/9780727763495>.

</div>

<div id="ref-paterson_horse_1926">

Paterson, James. 1926. “Horse Transport and Motor Transport.” *RSA
Journal* 74 (3837): 689–702.

</div>

<div id="ref-pebesma_simple_2018">

Pebesma, Edzer. 2018. “Simple Features for R: Standardized Support for
Spatial Vector Data.” *The R Journal*.
<https://journal.r-project.org/archive/2018/RJ-2018-009/index.html>.

</div>

<div id="ref-pebesma_software_2015">

Pebesma, Edzer, Roger Bivand, Paulo Justiniano Ribeiro, and others.
2015. “Software for Spatial Statistics.” *Journal of Statistical
Software* 63 (1): 1–8.
<http://brage.bibsys.no/xmlui/bitstream/id/320781/Pebesma_Bivand_Ribeiro.pdf>.

</div>

<div id="ref-pucher_making_2008">

Pucher, John, and Ralph Buehler. 2008. “Making Cycling Irresistible:
Lessons from the Netherlands, Denmark and Germany.” *Transport Reviews*
28 (4): 495–528. <https://doi.org/10.1080/01441640701806612>.

</div>

<div id="ref-qgis_development_team_qgis_2019">

QGIS Development Team. 2019. “QGIS Geographic Information System.”
<http://qgis.osgeo.org>.

</div>

<div id="ref-r_core_team_r:_2019">

R Core Team. 2019. “R: A Language and Environment for Statistical
Computing.” <https://www.R-project.org/>.

</div>

<div id="ref-rodrigue_geography_2013">

Rodrigue, Jean-Paul, Claude Comtois, and Brian Slack. 2013. *The
Geography of Transport Systems*. Third. London, New York: Routledge.

</div>

<div id="ref-rossum_python_1995">

Rossum, Guido. 1995. “Python Reference Manual.” Amsterdam, The
Netherlands, The Netherlands: CWI (Centre for Mathematics; Computer
Science).

</div>

<div id="ref-rowlingson_rasp:_2003">

Rowlingson, Barry, Adrian Baddeley, Rolf Turner, and Peter Diggle. 2003.
“Rasp: A Package for Spatial Statistics.” In *Proceedings of the 3rd
International Workshop on Distributed Statistical Computing*, edited by
Kurt Hornik.
<https://www.r-project.org/conferences/DSC-2003/Proceedings/RowlingsonEtAl.pdf>.

</div>

<div id="ref-shankari_e-mission:_2018">

Shankari, K., Mohamed Amine Bouzaghrane, Samuel M. Maurer, Paul Waddell,
David E. Culler, and Randy H. Katz. 2018. “E-Mission: An Open-Source,
Smartphone Platform for Collecting Human Travel Data.” *Transportation
Research Record* 2672 (42): 1–12.
<https://doi.org/10.1177/0361198118770167>.

</div>

<div id="ref-te_brommelstroet_developing_2008">

te Brömmelstroet, Marco, and Luca Bertolini. 2008. “Developing Land Use
and Transport PSS: Meaningful Information Through a Dialogue Between
Modelers and Planners.” *Transport Policy* 15 (4): 251–59.
<https://doi.org/10.1016/j.tranpol.2008.06.001>.

</div>

<div id="ref-tennekes_tmap:_2018">

Tennekes, Martijn. 2018. “Tmap: Thematic Maps in R.” *Journal of
Statistical Software, Articles* 84 (6): 1–39.
<https://doi.org/10.18637/jss.v084.i06>.

</div>

<div id="ref-timms_imagineering_2014">

Timms, Paul, Miles Tight, and David Watling. 2014. “Imagineering
Mobility: Constructing Utopias for Future Urban Transport.” *Environment
and Planning A* 46 (1): 78–93. <https://doi.org/10.1068/a45669>.

</div>

<div id="ref-transport_systems_catapult_transport_2015">

Transport Systems Catapult. 2015. “The Transport Data Revolution.”
Government. Transport Systems Catapult.
<https://ts.catapult.org.uk/wp-content/uploads/2016/04/The-Transport-Data-Revolution.pdf>.

</div>

<div id="ref-trewartha_japanese_1934">

Trewartha, Glenn T. 1934. “Japanese Cities Distribution and Morphology.”
*Geographical Review* 24 (3): 404–17. <https://doi.org/10.2307/208912>.

</div>

<div id="ref-venables_modern_2002">

Venables, W. N., and B. D. Ripley. 2002. *Modern Applied Statistics with
S*. Fourth. New York: Springer. <http://www.stats.ox.ac.uk/pub/MASS4>.

</div>

<div id="ref-world_health_organization_global_2018">

World Health Organization. 2018. *Global Status Report on Road Safety
2018*. S.l.
<https://www.who.int/violence_injury_prevention/road_safety_status/2018/en/>.

</div>

<div id="ref-xie_evolving_2011">

Xie, Feng, and David Levinson. 2011. *Evolving Transportation Networks*.
Transportation Research, Economics and Policy. New York:
Springer-Verlag. <https://www.springer.com/gp/book/9781441998033>.

</div>

<div id="ref-zandbergen_python_2015">

Zandbergen, Paul A. 2015. *Python Scripting for ArcGIS*. Esri press.

</div>

</div>

1.   Articles about successful transport planners illustrate the point.
    Ben Hamilton-Baillie (1955 - 2019), for example, was an influential
    transport planner and street designer whose obituary stated that
    “hundreds of thousands of people who are safer and happier as a
    result of his achievements” (Tim Stornor, quoted in
    [TransportExtra](https://www.transportxtra.com/publications/local-transport-today/news/60655/obituary-ben-hamilton-baillie/)).

2.  Transport is a major electoral issue in London and the current
    Mayor, Sadiq Kahn, has made tackling air pollution a policy
    priority. See
    [tfl.gov.uk/corporate/about-tfl/the-mayors-transport-strategy](https://tfl.gov.uk/corporate/about-tfl/the-mayors-transport-strategy).

3.   The current Mayor of Paris, Anne Hidalgo, sees transport as a
    priority and has plans to make public transport free. See
    [paris.fr](https://www.paris.fr/rechercher/transport).

4.   Bogotá has an innovative and prominent transport policy, led by the
    two times mayor Enrique Peñalosa, who has led the roll-out of major
    bus and cycleway projects in the city. See
    [sitp.gov.co](https://www.sitp.gov.co/).

5.   UTPS stands for the UMT (Urban Mass Transportation Administration,
    an agency of the DoT responsible for transport planning)
    Transportation Planning System (UTPS) and PLANPAC

6.   Like Python packages, R packages are analogous to Apps on
    smartphones and plugins in QGIS (described below), that provide new
    functionality. Many implement recently developed statistical and
    computational techniques (some of which are accompanied by papers
    describing new methods in academic journals such as the *Journal for
    Statistical Software*) or provide interfaces to software written in
    other languages, meaning that R can provide transport researchers
    with access to many cutting-edge methods via a single system.

7.   The author has first hand experience of the costs of
    context-switching: during my PhD I used R for the statistical and
    modelling analysis, and then switched to QGIS for geographic
    analysis and visualisation. While this approach worked well, the
    cognitive burden of having to learn and manage two substantial
    programs was substantial.
