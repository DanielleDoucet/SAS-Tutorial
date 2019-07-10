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

##Put Function
_put function takes a numberic variable and changes it to a character

`data diseasereal; 
set disease;
diagdesc=put(diagcode,$codetwo.);
run;`

**Code broken down**
data diseasereal; _<-create a new data set called 'diseasereal'
set disease; _<- telling SAS you want to use the data in the existing data set 'disease'
diagdesc=put(diagcode,$codetwo.); _<-creating a new variable called 'diagdesc' and 'putting' (diagcode,$codetwo.) inside it

### Whole Code
`data disease;
input diagcode$;
datalines;
001
290
800
;
run;

proc print data=disease;
run;

proc format;
value $codetwo
"001" = 'Malaria'
"290" = 'Social Anxiety Disorder'
"800" = 'Leg Injury';
run;

data diseasereal; 
set disease;
diagdesc=put(diagcode,$codetwo.);
run;

proc print data=diseasereal;
run;`


##Input Function
_input function takes a character variable and changes it to a numeric
_different than the input statement

  `data testin;
      input sale $9.;
      fmtsale=input(sale,comma9.);
      datalines;
   2,115,353
   ;`

input funtion converts a charater to a numberic value and stores it in another variable. 
The Comma9. informat reads the value of SALE and strips it of commas
The resulting value, 2115353 is stored in FMTSALE


## User Defined Formats
proc format

**just code**
`data disease;
input diagcode$;
datalines;
001
290
800
;
run;

proc print data=disease;
run;

proc format;
value $codetwo 
"001" = 'Malaria'
"290" = 'Social Anxiety Disorder'
"800" = 'Leg Injury';
run; 

proc print data=disease;
format diagcode $codetwo.;
run;`


**code with descriptions**
`proc format;
value $codetwo /*rename the data as codetwo*/
"001" = 'Malaria'
"290" = 'Social Anxiety Disorder'
"800" = 'Leg Injury';
run; /*you want  the code but also what the code represents*/

proc print data=disease;
format diagcode $codetwo.;/*you need the dot at the end to signify a format*/
run;`

With this format you do not see the code, only what you have formatted the code to signify




