# Outlier-Removal-techniques-ML


Explaination of the remove_bhk_outliers function:

Inner for loop will iterate for every possible group of no. of bedrooms of that respective  location group. (of outer for loop)


First inner for loop will store information about mean , std and no of data points( no of values present in a group of bedroom) in the already created dictionary in the outer for loop with key as the respective bedroom no. group. i.e (bhk_stats[2] stores info about 2 bedroom group values)


Second inner for loop performs the main functionality,
stats = bhk_stats.get(bhk-1)


here it will fetch the value for the previous no. of bedroom group.
For example, for 1 bedroom group it will be None , as there is no possibe value stored for 0 bedroom group, simply because there is not any value like that in dataframe.


also for 3 bedroom group, it will fetch information about 2 bedroom group ( so that we can check the mean value )


if stats and stats['count']>5:
it checks if there is dictionary present ( we didn't have for 1 bedroom group ) because None value will throw error. It also checks if it has more than 5 values or not. Because we cannot decide to discard something without comparing it with substantial data values.


exclude_indices = np.append(exclude_indices, bhk_df[bhk_df.price_per_sqft<(stats['mean'])].index.values)
this will finally store the index of the current bedroom group's element if it is lower than the previous bedroom's mean value..


then they are dropped
