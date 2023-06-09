####Identifier Type	Rules for Naming	Examples
###JAVA
#####Packages

The prefix of a unique package name is always written in all-lowercase ASCII letters and should be one of the top-level domain names, currently com, edu, gov, mil, net, org, or one of the English two-letter codes identifying countries as specified in ISO Standard 3166, 1981.
Subsequent components of the package name vary according to an organization's own internal naming conventions. Such conventions might specify that certain directory name components be division, department, project, machine, or login names.

**com.sun.eng
com.apple.quicktime.v2
edu.cmu.cs.bovik.cheese**

#####Classes	
Class names should be nouns, in mixed case with the first letter of each internal word capitalized. Try to keep your class names simple and descriptive. Use whole words-avoid acronyms and abbreviations (unless the abbreviation is much more widely used than the long form, such as URL or HTML).	class Raster;
class ImageSprite;
#####Interfaces	
Interface names should be capitalized like class names.	
interface **RasterDelegate**;
interface **Storing**;
#####Methods	
Methods should be verbs, in mixed case with the first letter lowercase, with the first letter of each internal word capitalized.	
**run();
runFast();
getBackground();**
#####Variables	
Except for variables, all instance, class, and class constants are in mixed case with a lowercase first letter. Internal words start with capital letters. 
Variable names should not start with underscore _ or dollar sign $ characters, even though both are allowed.
Variable names should be short yet meaningful. The choice of a variable name should be mnemonic- that is, designed to indicate to the casual observer the intent of its use. One-character variable names should be avoided except for temporary "throwaway" variables. Common names for temporary variables are i, j, k, m, and n for integers; c, d, and e for characters.

**int             i;
char            c;
float           myWidth;**
#####Constants	
The names of variables declared class constants and of ANSI constants should be all uppercase with words separated by underscores ("_"). (ANSI constants should be avoided, for ease of debugging.)	
**static final int MIN_WIDTH = 4;
static final int MAX_WIDTH = 999;
static final int GET_THE_CPU = 1;**

###MYSQL
Using lowercase will help speed typing, avoid mistakes as MYSQL is case sensitive.

Space replaced with Underscore — Using space between words is not advised.

Numbers are not for names — While naming, it is essential that it contains only Alpha English alphabets.

Valid Names — Names should be a descriptive of the elements. i.e. — Self-explanatory and not more than 64 characters.

No prefixes allowed.

####MYSQL Table Name
Lower Case Table Name
Table name in Singular
####Field Names
Use all above cases which include lowercase, no space, no numbers, and avoid prefix.

Choose short names no-longer than two words.

Field names should be easy and understandable.

Primary key can be id or table name_id or it can be a self-explanatory name.

Avoid using reserve words as field name. i.e. — Pre-defined words or Keywords. You can add prefix to these names to make it understandable like user_name, signup_date.

Avoid using column with same name as table name. This can cause confusion while writing query.

Avoid abbreviated, concatenated, or acronym-based names.