# ParquetGenerator
A single HTML page that will generate randomized parquet data in your browser based on a configured schema

This will be a single page 'application' with no backend that has a form that allows a user to enter a definition for a parquet schema, generate data for that schema and provide a parquet file for download.

## Required Fields:

- Name for the dataset
- Number of rows
- A table editor for columns
- A submit button

## Column Editor

The table editor shall be list-like and require a name for the column and a select box of allowable datatypes. Along with each column, it should allow things like telling if the value is a key you would group on, if there is a constant value, 
if there's an interval to the values, whether there should be bounds, if the values should be ordered, and if there should be a template for string types.

### Group Keys

Some data, such as collections of time series will have repetitive values, such as locations and dates. If you have columns such as `"date"`, `"location"`, and `"site"`, you'd want to generate a set of dates that will be reused for each 
location across each site, creating permutations of each.

### Intervals

If working with strings or dates, you may want intervals of different types. With dates, you may want to say "start at 1970-01-01" and "increment by an hour" and with strings you may want to say "start with the number `1` to feed into a template and end with the number `77`".

### Templates

When working with strings, you may want to specify a template to show a general idea of how they should look. If I'm generating location names, for example, I may want to have a template like `Location {}`, where a number or letter from the interval gets subbed into `{}`.

### Ordering

You should only be able to order columns that are group keys, but you should be able to specify that columns like dates should be in ascending order

### Constants

Some fields may need constant values. You may need fields for unit names or variable names, or just columns that need to look like something but whose values don't factor into anything.

### Bounds

If you're generating random numbers, having values being from -infinity to infinity may be too unrealistic for experiments. Adding in bounds to say "My values should be from `150` to `300`" would make the generated data look more natural.
