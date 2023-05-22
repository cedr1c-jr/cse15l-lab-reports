**Lab Report 3**

I chose to do the grep command for this lab report. Normally, the grep command searchers a file for a
given pattern and prints any lines containing this pattern.

I found all of these options using the man grep command in my terminal.

**-f option**

This option takes a file and uses it as the pattern to search. This is useful when you already have a file with
a list of things you want to search for instead of typing them all into the terminal.

    find technical > find-results.txt
    grep -f pattern1.txt find-results.txt > grep-results.txt
    
Inside the pattern1.txt file is just 1 line that reads "chapter".

Here is the output in the grep-results.txt file.

    technical/911report/chapter-13.4.txt
    technical/911report/chapter-13.5.txt
    technical/911report/chapter-13.1.txt
    technical/911report/chapter-13.2.txt
    technical/911report/chapter-13.3.txt
    technical/911report/chapter-3.txt
    technical/911report/chapter-2.txt
    technical/911report/chapter-1.txt
    technical/911report/chapter-5.txt
    technical/911report/chapter-6.txt
    technical/911report/chapter-7.txt
    technical/911report/chapter-9.txt
    technical/911report/chapter-8.txt
    technical/911report/chapter-12.txt
    technical/911report/chapter-10.txt
    technical/911report/chapter-11.txt
    
I can use the wc command to just print the amount of lines / words / characters in a file.

    wc grep-results.txt
    
Which gives:

    16      16     562 grep-results.txt
    
If the output is too big I might just show the wc output instead of copying all the lines grep outputs.

Here is the second example of -f:

    find technical > find-results.txt
    grep -f pattern1.txt find-results.txt > grep-results.txt
    
pattern1.txt has been changed to read "journal".

Here is the output from wc grep-results.txt:

    102     102    4080 grep-results.txt
    
**-v option**

This option inverts the results from grep, so any files not containing the pattern will now be the output. This is
when you need to exclude certain files from your output.

    find technical > find-results.txt
    grep -v ".txt" find-results.txt > grep-results.txt
    
This output of this command will be any lines not containing ".txt".

    technical
    technical/government
    technical/government/About_LSC
    technical/government/Env_Prot_Agen
    technical/government/Alcohol_Problems
    technical/government/Gen_Account_Office
    technical/government/Post_Rate_Comm
    technical/government/Media
    technical/plos
    technical/biomed
    technical/911report
    
Output from wc:

    11      11     290 grep-results.txt
    
Here is the second example:

    find technical/911report > find-results.txt
    grep -v "-" find-results.txt > grep-results.txt
    
And the output:

    technical/911report
    technical/911report/preface.txt
    
If the output is short enough I won't show the wc output. Actually I realize I can just limit
the search of grep with stricter patterns and specific folders...

**-m option**

The -m option takes a number (NUM) and only prints the first NUM lines that match the pattern.
This is useful when you don't need all the files the match and only the first few. Or if there are wayyy too many files
that come up with the given pattern.

    find technical > find-results.txt
    grep -m 10 ".txt" find-results.txt > grep-results.txt
    
This is the output:

    technical/government/About_LSC/LegalServCorp_v_VelazquezSyllabus.txt
    technical/government/About_LSC/Progress_report.txt
    technical/government/About_LSC/Strategic_report.txt
    technical/government/About_LSC/Comments_on_semiannual.txt
    technical/government/About_LSC/Special_report_to_congress.txt
    technical/government/About_LSC/CONFIG_STANDARDS.txt
    technical/government/About_LSC/commission_report.txt
    technical/government/About_LSC/LegalServCorp_v_VelazquezDissent.txt
    technical/government/About_LSC/ONTARIO_LEGAL_AID_SERIES.txt
    technical/government/About_LSC/LegalServCorp_v_VelazquezOpinion.txt
    
Here is the second example:

    find technical/911report > find-results.txt
    grep -m 5 "chapter" find-results.txt > grep-results.txt
    
And the output:

    technical/911report/chapter-13.4.txt
    technical/911report/chapter-13.5.txt
    technical/911report/chapter-13.1.txt
    technical/911report/chapter-13.2.txt
    technical/911report/chapter-13.3.txt

**-c option**

The -c option suppresses the normal input and only prints a number which corresponds to the number of lines that
contain the pattern. This is useful when you only need to know the number of files/lines that contain the pattern
but don't need to know exactly which ones.

    find technical/911report > find-results.txt
    grep -c "chapter" find-results.txt > grep-results.txt
    
The output:

    16
    
Second example:

    find technical/plos > find-results.txt
    grep -c "pmed" find-results.txt > grep-results.txt
    
The output:

    150
