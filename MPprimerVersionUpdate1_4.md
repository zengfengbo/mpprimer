# Introduction #

This wiki describes the changes of MPprimer-1.4 version and why users should use this version for multiplex PCR primers design.

# Main changes #

**In this version of MPprimer, there will be a matrix created by MPprimer every time when designing primers.**

# Why: user's valuable questions and comments #

(1). **What is simplest way to find a larger compatible group of target sequences? I was simply doing fairly random collections to find the largest number for which I could obtain PSCs. (from Phillip Shaw)**

> Before this version, there is no simple way to find the largest compatible group for the templates. And this deficiency bring too much trouble for the users. After email talk with  Phil (a user of MPprimer), I realized that this is an important and urgent problem. So I updated the MPprimer to 1.4 version. In this version of MPprimer, there will be a matrix created by MPprimer every time when designing primers. This matrix contains values between 0 and 1 for indicating the compatibility of each two templates. If two templates has an matrix value of "0" or closer to "0", that means they are compatible. Otherwise, if the matrix value is "1" or closer to "1", that means they can not be grouped into one group. By inspecting this matrix, we can find out the template(s) which can not be grouped into one group with other templates. According to this matrix, we can split the templates into two or more groups manually. Although this is not an automatics way and requires much patience, it's really a solution for the problem. In my laboratory, this matrix is very helpful and efficient when I designing multiplex PCR primers.

(2). **What does it mean when in the output "****MFEprimer specificity checking result. No MFEprimer specificity checking result is available." Do I have to independently check the primer pairs by MFE primer via the webserver if on the linux version we are getting this message?**

> " MFEprimer specificity checking result. No MFEprimer specificity checking result is available." - This message indicate that you do not evaluate the primers with MFEprimer program. But you do not have to check the primers by MFEprimer via the web server, just add the option "-d database\_name" when you using MPprimer designing primers. MPprimer has already included MFEprimer as an function for primers specificity evaluation. This is an example:

> $: ./MPprimer.py -i Phil\_example\_seq.p3 -o Phil\_example\_seq.mp -m 0bp -d Homo\_sapiens.rna

> Note: Homo\_sapiens.rna is the Human RefSeq mRNA database downloaded from NCBI ftp site. (The database need to be formated by formatdb command from NCBI-BLAST software. Or you can use the "formatdb" from "MPprimer/MFEprimer/bin" directory.)

> Optionally, If you want to evaluate the primers separately, the package of command line version of MFEprimer has already included in the directory of MPprimer. You can "cd" into "MPprimer/MFEprimer" for details.

# How to use the matrix for grouping the templates #

Below is the matrix in the "MPprimer/test" directory, users can view it by Excel or other similar softwares.

| |	**Mus\_AQP2**|	**Mus\_AQP11**|	**Mus\_AQP12**|	**Mus\_AQP6**|
|:|:-------------|:--------------|:--------------|:-------------|
|**Mus\_AQP2**|	0            |	0.04          |	0.08          |	0            |
|**Mus\_AQP11**|	0.04         |	0             |	0             |	0            |
|**Mus\_AQP12**|	0.08         |	0             |	0             |	0            |
|**Mus\_AQP6**|	0            |	0             |	0             |	0            |

In this table, the four templates are compatible based on the matrix values (They all are 0 or closer to 0). However, if the value in (row 1, col 2) is 1, it means that Mus\_AQP2 and Mus\_AQP11 are not compatible and they can not be in a group, one of them should be removed.

# Acknowledgements #

**Phillip Shaw**

# Any questions? #

Any questions or comments please email to Wubin Qu <quwubin@gmail.com> or leave the message here.