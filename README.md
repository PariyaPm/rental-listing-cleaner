rental-listing-cleaner
The R scripts that perform the data cleaning for Rental Listings project
This repository includes two R scripts: Data_prep.R and main.
Data_prep includes several functions of:
**clean_raw_listing -> takes the raw listing as the only argument and cleand the whole dataset by removing meaningless listings, duplicates, listings with none in title, listings with asking price of greater than 50,000 and smaller than 300.  The words with the same meaning will substitute and spatial locations will add of neighborhood, town, census tract, community type will be added to the attributes of the table.  Duplicate_finder -> listing is the argument that should be passed to this function. possible duplicates (listingDup) will be identified according to the txt distance of titles, number of bedrooms and asking prices.  
**remove_duplicates -> this function takes the listing and possible duplicates (listingDup) and removes the possible duplicates which are from craigs list and also removes padmapper listings which have identical titles/asking price/num bedroom  
**n_gram_builder -> builds the ngrams based on n value  spatial_locator -> assigns the location in which any of the records fall. the location attribute  consists of: town, community type, census tract and neighborhood  Room_analysis -> analysis the data and besed on the arguments of  +keywrdlst: the vector of keywords possibly indicate the target group +listing: the listings which require to be processed +name: the name of the field to be added to the table +br: expected number of bedrooms in the bedrooms field +numBR: the value for num_bedrooms that we want to set +num: the threshold of #of records per neighborhood adds two columns of whether the data is in the target group or not (binary), if the asking price is within the specific range, lower than or above the range (-1,0,+1), the results will be saved in a file.  Threshold_finder -> finds the range of the asking prices for the whole data  neighborhood_stat ->  finds the range of the asking price based on neighborhood  
**comm_type_rent_stat -> finds the range of the asking prices for based on community type  
**town_rent_stat -> finds the statistics and range of price based on town  
**exclude_recs -> takes the listing and vector of excluding words and returns all the listings which do not have excluding words in the title  
**comb -> combines specific words to create meaningfill phrases for each category of data (such as "TWO BEDROOM ONE BATHROOM CONDO")  
**sample.DF -> gets the listing (x) and percentile and returns the sample of percentile size  main.R code includes al the fuction calls of the Data_prep.
