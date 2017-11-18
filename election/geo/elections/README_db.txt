Contacts:
Alex Charles Takata - act444@nyu.edu
Feng Shen - fs1412@nyu.edu
Lihua Xiong - lx559@nyu.edu

Naming Convention:
For each elections/YYYY folder,
	- general.csv contains results for general election in YYYY.
	- primary.csv contains results for primary election in YYYY.
	- xxxx_FIPS.csv contains extra fields of FIPS and state abbreviations.

For each .csv file, the following fields exist,
	- state, county: state and county name
	- 1nd, 2nd, 3rd: the names of the top, second and third candidate (nan if no third
	candidate)
	- votes1, votes2, votes3: the number of votes for the top, second and third candidate
	- pct1, pct2, pct3: percentage votes of the top, second and third candidate
	- party1, party2, party3: party of the top 3 candidates e.g. D / R / O (democrats,
	republicans or other)
	- FIPS: only in xxxx_FIPS.csv, the FIPS of corresponding county
	- Abbreviation: only in xxxx_FIPS.cvs, the state abbreviation

Note:
	- There are NaNs in the dataset.
	- We only find primary election results for 2016.
	- For 2008 dataset, the general_Wiki.csv is scrapped from Wikipedia but a lot of 	counties are missing. We further scrapped from the NYT website and merged the two 	datasets to create the general_FIPS.csv file.