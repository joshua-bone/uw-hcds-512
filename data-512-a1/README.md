# Joshua Bone
### A1 - Data Curation
#### UW - DATA 512 - 2018-10-14

##### Goal:
The goal of this project, from the 
[assignment description](https://wiki.communitydata.cc/Human_Centered_Data_Science_(Fall_2018)/Assignments#A1:_Data_curation),
is to "Construct, analyze, and publish a dataset of monthly traffic on English Wikipedia from 
January 1 2008 through September 30 2018."

##### Instructions: 
Run 'hcds_a1_data_curation.ipynb' as a Jupyter notebook.
Run all cells to call the APIs and run the entire workload from scratch. 
All files other than the Jupyter notebook will be overwritten.
<p> 
If the wikipedia APIs are unavailable, or if Internet access is restricted,
change the line in the 2nd cell from 'USE_CACHED_API_RESULTS = False'
to 'USE_CACHED_API_RESULTS = True'. This will not attempt any API calls, and
will use the cached JSON files in this directory as the starting point instead.

##### Source Data:
The source data is obtained from the Wikimedia Foundation 
"[Analytics/AQS/Legacy Pagecounts](https://wikitech.wikimedia.org/wiki/Analytics/AQS/Legacy_Pagecounts)" 
and 
"[Analytics/AQS/Pageviews](https://wikitech.wikimedia.org/wiki/Analytics/AQS/Pageviews)" APIs, which are
licenced under the Creative Commons CC-BY-SA license
(See [Terms and Conditions](https://www.mediawiki.org/wiki/REST_API#Terms_and_conditions)).

##### Final Data:
The final deliverable is this visualization:
![](hcds-a1-visualization.png?raw=true)
<p> The data for this visualization is in the output file "en-wikipedia_traffic_200701-201809.csv",
contained within this directory. 
The CSV file containes 8 columns:
<ul>
<li>year: The year this row of data belongs to. (4 digit integer)
<li>month: The month this row of data belongs to. (2 digit integer)
<li>pagecount_all_views: The total views from all platforms (desktop + mobile) for this bucket, from the Legacy API. (integer)
<li>pagecount_desktop_views: The total views from desktop platforms for this bucket, from the Legacy API. (integer)
<li>pagecount_mobile_views: The total views from mobile platforms for this bucket,from the Legacy API. (integer)
<li>pageview_all_views: The total views from all platforms (desktop + mobile) for this bucket, from the Pageviews API. (integer)
<li>pageview_desktop_views: The total views from desktop platforms for this bucket, from the Pageviews API. (integer)
<li>pageview_mobile_views: The total views from mobile platforms for this bucket, from the Pageviews API. (integer)
<p> It should be noted that the data from the Pageviews API has been filtered to remove views from internet bots.
This can be seen from the fact that the total views from all platforms for the Pageviews API is lower than that of 
the Pagecount API during the overlapping period from mid-2015 to mid-2016.
<p> Also, data from the first and last month of the Legacy API (December 2007 and August 2016) are not shown, 
as they appear to represent partial months of data. 
