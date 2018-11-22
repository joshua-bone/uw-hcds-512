# A4: Final Project Plan - Effect of 2018 U.S. Elections on Wikipedia Views and Edits For U. S. Congressional Candidates

Joshua Bone  
DATA 512  
University of Washington  
22 November 2018

## Introduction
This project will study how often the Wikipedia pages of U.S. Congressional candidates were viewed and revised during the time period leading up to and including the 2018 elections. It will attempt to compare the information by political party, and possibly by how closely contested the election was according to pre-election polling. The intention of the study is to determine whether there are observable differences or biases between political parties, and whether these differences are heightened when the election is closely contested.

I am planning to do this analysis because I think that Wikipedia is widely used as one of the first places to go to find information about a political candidate, and because it is seen as a relatively unbiased source. I suspect that the vast majority of people who view Wikipedia pages are unaware of the constant changes and revisions that are being made behind the scenes. Because anyone can make edits to the content, and because a politician's Wikipedia page is likely the first landing point for information for many prospective voters, it can be imagined that effort is actively made by both supporters and detractors of the candidate to edit the information in a way that is beneficial to their side. While Wikipedia's [Protection Policy](https://en.wikipedia.org/wiki/Wikipedia:Protection_policy#extended) no doubt does much to prevent the site from being used as a mudslinging platform, a simple glance at the [revision history](https://en.wikipedia.org/w/index.php?title=Donald_Trump&offset=&limit=500&action=history) for Donald Trump's Wikipedia page (to use an obviously polarizing example), as well as the [Talk page](https://en.wikipedia.org/wiki/Talk:Donald_Trump) for that article, shows a near-constant back-and-forth of revisions and community discussion about what information should be shown, and where.

I think this analysis will be interesting from a human-centered point of view because of how it will either challenge or reinforce our conception of Wikipedia as being an unbiased source of information. I hope that it will additionally raise awareness about how Wikipedia is an active project that is constantly changing with current events.

## Research Questions
#### Do trends in Wikipedia page views and edits vary between political parties?
My hypothesis is that, while individual biases are undoubtedly present in the data, overall there will be similar trends between the two parties.

#### Do trends in Wikipedia page views and edits vary with how contested an election is believed to be?
My hypothesis is that there is a strong correlation, i.e. that elections that are perceived to be highly contested result in more page views and edits.

#### How do trends in Wikipedia page views and edits vary over the course of an election cycle?
My hypothesis is that there is a steadily increasing buildup of activity with a peak occuring just after the election date.

## Data
#### Politicians
I had trouble finding an appropriately licensed dataset of the 2018 Congressional candidates. Unless I can find a better source, my politician data will be gleaned from two tables found on the Wikipedia articles for the 2018
[US House](https://en.wikipedia.org/wiki/United_States_House_of_Representatives_elections,_2018#Latest_published_ratings_for_competitive_seats)  and
[US Senate](https://en.wikipedia.org/wiki/United_States_Senate_elections,_2018#Pre-election_predictions) races. The US Senate table contains all 35 of the elected Senators (with the exception of the Mississippi race, which remains TBD at the time of this writing), while the US House table contains only the approximately 30% of the House seats (for a total of 138 rows) which were deemed to be "competitive" by at least one of six pre-election rating groups. (For the purposes of this study there is no need for an exhaustive list; a subset will work just as well).

Both tables contain considerably more data than I need for this study, including information on which seat the candidates were running for, the pre-election predictions from each of six rating groups, the Cook Partisan Voting Index (measuring the relative political leaning of the represented region), the incumbent politician, and the voting percentage of the previous election. Currently the only information I plan to use from either table is the name of each winning politician, their political party, and the link to their wikipedia page; however, I may also try to measure how closely contested the election was believed to be by averaging the pre-election predictions as well. 

Since this data is embedded in a Wikipedia page, I will either have to find a way to copy the data from the page via a script (preferred for ease of reproducibility) or else copy and paste the data by hand into a spreadsheet, which can then be saved to CSV. 

Like all of Wikipedia's text content, this data is licensed under the [CC-BY-SA 4.0](https://creativecommons.org/licenses/by-sa/4.0/) license. 


#### Wikimedia Pageview API
This API returns the number of times that a Wikipedia page was viewed during a specified time period. (Details and example API calls can be found [here](https://wikitech.wikimedia.org/wiki/Analytics/AQS/Pageviews)). The data from this API is licensed under the [CC-BY-SA 3.0](https://creativecommons.org/licenses/by-sa/3.0/).

I intend to use this API to return the count of daily views for each politician's Wikipedia page over a period of time leading up to and including the 2018 midterm elections.

#### Mediawiki API
This API has a query module that returns, among other things, a history of revisions for a Wikipedia page, including the editor's username, the timestamp of the revision, and a comment explaining which changes were made. (Details and example API calls can be found [here](https://www.mediawiki.org/wiki/API:Query)). The data from this API is licensed under the [CC-BY-SA 3.0](https://creativecommons.org/licenses/by-sa/3.0/) license.

I intend to use this API to return the revision history for each politician's Wikipedia page, which I will then aggregate to find the count of daily revisions for each page over a period of time leading up to and including the 2018 midterm elections. 

## Plan
I intend to use a Jupyter notebook backed by a Python 3.6 runtime environment for this analysis. I will process the data into the following two datasets, which I can join together at runtime.

#### Candidate Dataset
This dataset will contain at least the following columns:
<ul>
  <li> Candidate
  <li> Political Party
  <li> Pre-election Level of Contestedness
</ul>
The level of contestedness will be averaged from the six sources in the table and aggregated into 3 buckets: Safe, Contested, and Tossup. 

#### Views and Edits Dataset
This dataset will contain approximately the following columns:
<ul>
  <li> Date
  <li> Candidate
  <li> Page Views
  <li> Page Revisions
</ul>
Because the number of daily revisions is expected to be much less than the number of views, I will likely make these separate datasets, with revisions lumped into weekly buckets. Or, I may keep them in the same dataset and aggregate page views into weekly buckets as well. The final decision will be made based on how the resulting visualizations turn out.
  
#### Planned Artifacts
I plan to create two time-series charts. For both charts, the x-axis will represent time, likely starting in January 2018 and ending at least a week after Election Day (November 6, 2018). On one chart, the y-axis will represent page views, and on the other it will represent page revisions. On each chart, I hope to plot six lines:
<ul>
  <li>Republican Candidate, Safe</li>
  <li>Republican Candidate, Contested</li>
  <li>Republican Candidate, Tossup</li>
  <li>Democratic Candidate, Safe</li>
  <li>Democratic Candidate, Contested</li>
  <li>Democratic Candidate, Tossup</li>
</ul>

Beyond this, I have several ideas for exploring the data that may or may not yield fruitful visualizations. For example, one metric that be interesting to calculate would be average number of views per revision. Is it relatively constant across all categories? Another visualization that I may include if it turns out to be interesting is a comparison of multiple metrics across all categories at a specific point in time, for example, Election Day.
