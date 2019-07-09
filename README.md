# SAS-Tutorial on Importing Files

# Importing Files
## CSV- "Comma Separated Values"
`data weightgain;
infile "/home/u39109509/weightgain.csv" DSD Missover firstobs=2;
input id sources$ type$ weightg;
run;`

_must use " " around the file name when importing a .CSV file

### DSD (Delimiter Sensitive Data)
    1. It ignores delimiters in data values enclosed in quotes
    2. It ignores quotation marks as part of your data
    3. It treats two consecutive delimiters in a row as a missing value e.g. 1,,2 where the value between 1 and 2 is missing
    
### First Obs
    This identifies the first observation that should be processed. 
    first obs=2 means the first observation is on the second line
    
### Identifying Character Values
    All character values should have $ at the end of them when **FIRST** mentioned

## 'TXT-Text Files'
`data salary;
infile '/home/u39109509/salary.txt';
input year salary; 
run;`  

_single apstrophes used to designate the location of the .txt file
_when identifying the names of the columns separate with a space, no delimiters 
    
## XLSX- Excel Files
`proc import out=salesdata datafile="/home/u39109509/Sample-Sales-Data.xlsx" DBMS=XLSX;
proc print data=salesdata; 
run;`

_proc import The IMPORT procedure reads external data and writes the data to a SAS data set 
_DBMS identifies the file type 


 ## SPSS
  `proc import datafile="/home/u39109509/p054.sav" out=p054;
  run;`
  _out= allows you to name your output information
