# Layout Problems

### Good:

- Multiple input field for Destination & Airline Selector
- Splash Page for login looks good
- The presenence of input validation

### Bad: 

- After a filter is loaded, it should be auto-applied
- In the multi inputs of the selectors the chips should only stack vertically

# Backend Problems

- 25 000 delayed flights seems to much
- The number of flights are delayed should be shown. Summed up minutes is not useful. 
  Average Delay would be of interest.

# Crawler Problems

- Number of flights are only crawled for the first day of each month
- Number of passengers is consistently too low (around 500 to 600).
- Only six airlines are found flying from NY to las vegas in 2015. It should be 14.
- "merged" airline names should not happen
