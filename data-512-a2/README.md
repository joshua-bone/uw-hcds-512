# A2 - Bias In Data
### Joshua Bone
#### UW - DATA 512 - 2018-11-01
##### Goal
The purpose of this assignment is to explore bias in the quality of English Wikipedia articles about politicians in various countries. (See the [assignment description](https://wiki.communitydata.cc/Human_Centered_Data_Science_(Fall_2018)/Assignments#A2:_Bias_in_data) for further details).

##### Instructions: 
Run '512a2.ipynb' as a Jupyter notebook.
Run all cells to used local cached data, retrieved by the author from the ORES API, or else change the USE_CACHED_API_RESULTS to equal False before running all cells, to make the API calls at runtime. (Be warned, runtime may be 5-10 minutes in this case). 

##### Summary
<p>Overall, the study was inconclusive. Some results showed likely bias, for example, 3 of the 4 largest countries in the world occupied the bottom 3 spots for numbers of high quality articles per capita, but the United States (the 3rd most populous country) did not show up on that list. The two countries at the top of the list for percentage of all articles that are high quality, North Korea and Saudi Arabia, seem like they could be in those spots due to their disproportionately high level of interest to the West (national security in the first case, and oil in the second). 
<p>However, I found the rest of the results completely surprising, even baffling. The factors I would have predicted to lead to a high percentage of high quality English articles would have been:
    
- GDP
- So-called 'first-world' status (i.e. the U.S., Canada, and the E.U.)
- English speaking countries

<p> In fact, I did find some support for my theories. The U.S. did appear on the list for percentage of articles that are high quality. However, it only placed at number 9. I found that 17 of the 46 countries having NO high quality political articles were African nations, including 7 of the top 9 countries by population in that category.
    
<p> Central African Republic, consistently ranked as one of the world's poorest and least developed countries, appeared at number 3, blowing all of my theories out of the water. In fact, 3 African countries appeared on that top 10 list, all of them ranking in the bottom half by GDP and GDP per capita of countries on that continent. The only European Union country to make the list was Romania, at number 4. I am unable to explain these results. 
    
<p> Additionally, there were surprising contrasts in the data. The country of Bhutan, a landlocked region in the Himalayas, ranked as number 6 on the percentage of articles that are high quality. However, its neighbor Nepal, 40 miles to the west, was tied with 45 other countries for last place, having no high quality political articles. 17 underdeveloped African countries did show up as having zero high quality articles. But then 3 others from this region made the top 10 list. 
    
<p> In summary, more research would be needed to draw any strong conclusions from this data. It would be a mistake to accept the results where they appear to confirm the hypothesized factors, without having an explanation for the strange outliers discovered in this study.
