#Read Me
# Input Types and Formats
Three types of input:

List input 

Column input 

Formatted input

## List Input
`data sales;
input Name$ Sales_1-Sales_4;
cards;
greg 10 2 40 0 
john 15 . 10 100 
lisa 50 10 15 50 
mark 20 0 5 20 
run;`

_the "input" statement declares the variables
_must use space delimitors for *list* input
_missing data is denoted by a period
_character information must be less than 8 character and contain no spaces
_dates and complex values should not be used with this format

## Column Inputs

`data sales;
input Name$1-4 Sales_1-Sales_4 @5;/*have to tell SAS that the name column goes from 1-4 and that the data starts at the 5th line*/
cards;
greg10 2 40 0 
john15 5  10 100 
lisa50 10 15 50 
mark20 0 5 20 
run;`

_column input is good for standard numeric data
_embeded commas or dates are non standard

_spaces are not required between values for column in put

## Formatted Input
`data police1;
infile "/home/u39109509/londonoutcomes.csv" DSD Missover firstobs=2;
length CrimeID $25 ReportedF $25 FallsW $25 Longitude 4 Latitude 4 Location $25 LSOAC $25 LSOAN $25 OutcomeT $25;
input CrimeID$ ReportedF$ FAllsW$ Longitude Latitude Location$ LSOAC$ LSOAN$ OutcomeT$;
run;`


_set length by adding $# in the length statement after input statement

_common date format MMDDYY10.;


