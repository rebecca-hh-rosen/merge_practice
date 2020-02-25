# A Focused Example of Panda’s DataFrame.merge Function


During a side project, I found myself running into troubles with the pandas.DataFrame.merge function. I saw duplication of some rows and not others, and it seemed that the function was filling in multiple instances of the smaller data frame into rows of the other. Because I just wanted to see NaN values there, so I took it as an opportunity to explore the merge function in greater depth and was able to see what was really going on.

Note: only Pandas and Numpy are the only packages necessary to follow along with this article.
Panda’s merge vs SQL’s join

## The Process:
To do this, I first generated 2 random data frames of size 100x3, each with 2 unique and 1 duplicate column. 

I then created an additional row in each of the data frames. These will track how unique instances in each data frame are handled in the merge. I chose the numbers 100 and 200 because I was certain it was not going to show up anywhere else, as the data frame is necessarily comprised of random integers 0–100 (not inclusive), and 100 is tracking df1 while df2 is tracking df2. This allows me to be certain about where the rows end up in the merge.

We’re good! Then I set out and see how these rows show up in different types of merges.

## Inner Merge:
An inner merge takes the intersection of keys from each data frame — the intersection of the Venn Diagram. As we can see, this means that neither of our unique rows were preserved.
Outer Merge

## Outer Merge:
An outer merge takes the union of keys from each data frame — the entire are of the Venn Diagram. As we can see, this means that both of our unique rows were preserved!


*However - what if we want to get one and not the other unique row? In come“left” and “right” merges.*

## Left Merge
Here we can see that only the unique row from df1, the one with the “A” value of 100, was preserved. Additionally, only the “B” and “C” columns have values, while the “D” and “E” columns from df2 are NaN values.

## Right Merge
Only the “A” value of 200 is maintained, along with the rest of the df2’s “D” and ”E” columns. The other “B” and “C” columns from df1 are NaN values. Success!

## Conclusion
In this example, we got up-close and personal to see the differences between the 4 types of data frame merges available in Pandas. There are many more parameters to explore, including the “how” parameter, which I will be talking about in a future blog post.


If you’d like to see this blog post in full, please check out [my blog post!](https://medium.com/@rebeccahhrosen/a-focused-example-of-pandas-dataframe-merge-function-a393b736892)


*Rebecca Rosen is a recent graduate of Flatiron’s Data Science Immersive with a background in Cognitive Science and non-profit management. She currently resides in NYC and makes music in her spare time. To see more of her work, or to say hi, search Medium, Instagram or Facebook with the tag @rebeccahhrosen.*
