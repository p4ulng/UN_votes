DSA2101 Group Project
================

#### Group name: sixpeople

# Introduction

The UNVotes dataset compiled by tidytuesday comprises data about the
voting history of various countries on UN resolutions and amendments
since the first meeting in 1946. Votes have been categorised using six
issues: Colonialism, Economic Development, Palestinian Conflict, Arms
Control and Disarmament, Human Rights and Nuclear Weapons and Nuclear
material.

The key question that our group intends to explore with this dataset is:
**How has the UN’s voting patterns evolved over time, and what notable
trends and times of division can be observed? How closely do countries’
votes on these issues align with major powers such as the United States
of America, China and Russia?** By exploring these trends, we aim to
reveal how international alliances change and where consensus or
division is present and how a country might change its stance across
time.

# Data Cleaning & Summary

We examined the **three separate datasets** in the UNVotes data:
**un_votes** (countries’ voting records), **un_roll_calls** (information
on each resolution) and **un_roll_call_issues** (showing the topic tags
associated with each resolution). All three datasets shared a common
key: **rcid**, which was then utilised in a series of left joins to
merge the three datasets into one. This allowed us to match a resolution
with its metadata (like date and description) and issue classifications.
Additionally, we extracted the years from every resolution date using
the mutate function in order to conduct analyses based on time. Below
are the final columns used for our data analysis.

**rcid**: Unique roll call ID for each resolution  
**country**: Name of the country casting the vote  
**country_code**: ISO alpha-2 country code (e.g., “US”, “CA”)  
**vote**: Factor with 3 levels (“yes”, “no”, “abstain”)  
**session**: Numeric identifier for the UN session  
**importantvote**: Integer flag (0/1) for important votes  
**date**: Date the vote took place (format: “1946-01-01”)  
**amend**: Integer flag (0/1) for amendments  
**para**: Integer flag (0/1) for paragraph votes  
**short**: Brief label for the resolution (e.g., “AMENDMENTS, RULES OF
PROCEDURE”)  
**descr**: Longer description of the resolution (e.g., “TO ADOPT A CUBAN
AMENDMENT TO THE UK PROPOSAL”)

Our exploration of voting trends from 1946 to 2020 revealed several
insights. In the earlier decades, Colonialism was the key issue, taking
up a significant proportion of UN resolutions. This aligned with the
move towards decolonisation efforts during that period. With Cold War
tensions in the 1970s, more of the resolutions targeted nuclear weapons
and their disarmament. In the 1980s, however, there was a marked
increase in resolutions about the Palestinian conflict as the situation
worsened in the Middle East. We also saw the rise and fall in the number
of resolutions targeting issues like economic development, arms control
and global inequality which could be tied to geopolitical events over
the years. While human rights issues gained more of a spotlight from the
1970s, it also emerged to be the most divisive issue with only an
average vote consensus percentage of 73%. This means that, on average,
each resolution targeting human rights issues saw more than a quarter of
the countries opposing the majority vote. To get this number, we looked
at each resolution, identified what the majority of countries voted
(e.g., ‘Yes’ or ‘No’), and calculated the proportion of countries that
aligned with that majority. By averaging this across all human
rights-related resolutions, we found that consensus was generally lower
compared to other issues. This relatively lower level of agreement among
countries made the issue an interesting candidate for further analysis.

# Plots and Data Visualisation

![](DSA2101-Project-Final_files/figure-gfm/unnamed-chunk-4-1.png)<!-- -->

**Fig 1:** The **stacked area chart** (Year on the x-axis, Resolution
Count on the y-axis, colored by Issue Category) was chosen to show how
the UN’s voting patterns have changed over time. It clearly illustrates
shifts in focus across different issues and the rise or fall in
resolution activity. This helps identify historical turning points and
changing global priorities.

The six **line charts** (Proportion of resolutions per year by issue
type) shows how the focus of UN resolutions has changed over time,
broken down by issue or conflict. This helps reveal shifting global
priorities and provides insight into how countries have aligned their
votes, particularly in relation to major powers like the United States,
China, and Russia.

From the stacked area chart, we can see notable surges in the number of
resolutions in the mid-1970s coinciding with decolonisation movements,
the 1973 oil crisis and the then-intensifying Cold War. This period was
then followed by a plateau in the number of resolutions following the
dissolution of the Soviet Union which led to another peak in the late
1990s due to humanitarian intervention efforts in Yugoslavia and Rwanda.
This analysis shows how global priorities shifted over time from issues
like colonialism and arms control (during the Cold War) to other issues
like human rights and economic development in the 1990s. Recent surges
around 2015 can be attributed to multiple crises like civil unrest in
Syria, migration challenges in Europe, climate change mitigation
negotiations and the adoption of UN Sustainable Development Goals.

![](DSA2101-Project-Final_files/figure-gfm/unnamed-chunk-5-1.png)<!-- -->

**Fig 2:** We also conducted a time-series analysis (using a line chart)
of international bloc alignments on human rights issues, using the US
vote as a reference. For each resolution, we measured if a bloc’s vote
aligned with the US (agreement = 1, disagreement = 0) and averaged these
results by year and bloc. This allowed us to track the evolution of
political alignment over time, addressing the main question of how
countries’ voting patterns align with major powers like the US.

The analysis from 1946 onwards shows similarities and deviations in
trends among geopolitical groups. For instance, the Group of Seven (G7)
and the North-Atlantic Treaty Organisation (NATO) members like Germany,
France, and Japan tend to hold similar positions on human rights issues.
In contrast, emerging geopolitical groups such as BRICS (Brazil, Russia,
India, China, South Africa) and certain countries in the Organization of
the Petroleum Exporting Countries (OPEC) like Saudi Arabia and Iran
generally show lower and more inconsistent alignment with Western
nations. This indicates a shift in international views and priorities,
where human rights issues may be overshadowed by concerns over
sovereignty and national development.

**Fig 3:** The interactive choropleth map visualizes each nation’s
alignment with the US on resolutions from 2005 to 2015, a period we
narrowed down due to an unusually high number of resolutions passed
during those years. The alignment score, calculated in the same way as
for blocs but applied to individual countries, highlights evolving
geopolitical alliances and shifts in voting patterns in response to
global priorities.

It’s easy to see that countries within the same geographic regions often
voted in similar ways, with noticeable patterns emerging across the
identified geopolitical blocs. Although most Western countries generally
align with the US on human rights issues, there was a sharp drop in
agreement in 2008. Further analysis revealed that this was largely due
to a surge in human rights resolutions related to the Israel-Palestine
conflict during that year. This issue proved especially divisive even
among Western blocs. Toward the end of the timeline in 2015, however, we
observed a trend of increasing alignment with the US on human rights
resolutions across more countries.

# Final Conclusion/Discussion

In conclusion, our analysis of UN voting trends from 1946 to 2020
reveals how global priorities and alliances evolved over time.
Colonialism and nuclear disarmament were central early on, followed by
an increased focus on the Palestinian conflict and human rights in the
1980s and 1990s. Human rights remained the most divisive issue, with
only 73% average consensus. Geopolitical events like the fall of the
Soviet Union and humanitarian crises influenced UN resolutions.
Different blocs, such as G7, NATO, BRICS, and OPEC, showed varying
alignments with the US, especially on human rights, with notable
divisions like the 2008 Israel-Palestine conflict. These trends
highlight the shifting dynamics of global cooperation and division.
