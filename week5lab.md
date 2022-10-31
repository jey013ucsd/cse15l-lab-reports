#-name

Useful for finding a specific file with a speicfic name

```
$ find technical -name chapter-1.txt
technical/911report/chapter-1.txt
```
Finds files with the name "chapter-1.txt"



```
$ find technical -name "*.java"

```
Finds all java files in techincal. Since there are none, nothing is outputted.




```
$ find technical/biomed -name "1468-6708-3-1.txt"
technical/biomed/1468-6708-3-1.txt
```
Finds files with the name "1468-6708-3-1.txt" in the biomed directory.

---

#-type

Useful for finding files of a specific type, such as finding a directory

```
$ find technical -type d
technical
technical/911report
technical/biomed
technical/government
technical/government/About_LSC
technical/government/Alcohol_Problems
technical/government/Env_Prot_Agen
technical/government/Gen_Account_Office
technical/government/Media
technical/government/Post_Rate_Comm
technical/plos
```
Finds all directories in technical.




```
$ find technical/government -type d
technical/government
technical/government/About_LSC
technical/government/Alcohol_Problems
technical/government/Env_Prot_Agen
technical/government/Gen_Account_Office
technical/government/Media
technical/government/Post_Rate_Comm
```
Finds all directories within /government




```
$ find technical/government/Post_Rate_Comm -type f
technical/government/Post_Rate_Comm/Cohenetal_comparison.txt
technical/government/Post_Rate_Comm/Cohenetal_Cost_Function.txt
technical/government/Post_Rate_Comm/Cohenetal_CreamSkimming.txt
technical/government/Post_Rate_Comm/Cohenetal_DeliveryCost.txt
technical/government/Post_Rate_Comm/Cohenetal_RuralDelivery.txt
technical/government/Post_Rate_Comm/Cohenetal_Scale.txt
technical/government/Post_Rate_Comm/Gleiman_EMASpeech.txt
technical/government/Post_Rate_Comm/Gleiman_gca2000.txt
technical/government/Post_Rate_Comm/Mitchell_6-17-Mit.txt
technical/government/Post_Rate_Comm/Mitchell_RMVancouver.txt
technical/government/Post_Rate_Comm/Mitchell_spyros-first-class.txt
technical/government/Post_Rate_Comm/Redacted_Study.txt
technical/government/Post_Rate_Comm/ReportToCongress2002WEB.txt
technical/government/Post_Rate_Comm/WolakSpeech_usps.txt
```
Finds all regular files in technical/government/Post_Rate_Comm.

---

