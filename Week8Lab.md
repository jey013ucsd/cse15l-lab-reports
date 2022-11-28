# Lab Report 5

grade.sh code:
```
# Create your grading script here

rm -rf student-submission
git clone $1 student-submission
echo "Finished Cloning"
cp TestListExamples.java student-submission/
cp -r lib student-submission/
cd student-submission/

if [ -f "ListExamples.java" ]; then
	echo "File Found"
else
	echo "ListExamples.java not found"
	exit
fi

javac -cp ".;lib/hamcrest-core-1.3.jar;lib/junit-4.13.2.jar" *.java 2> error.txt


if [ $? -eq "0" ]; then
       echo "Code Compiled"	
else
	echo "Compile Error:"
	cat error.txt
	exit
fi

java -cp ".;lib/junit-4.13.2.jar;lib/hamcrest-core-1.3.jar" org.junit.runner.JUnitCore TestListExamples > tests.txt
echo "Tests run"


FAILED=$(grep -c "at TestListExamples" tests.txt)
SCORE=$((2 - $FAILED))
echo "You failed $FAILED tests, you have a score of $SCORE/2"

if [[ $FAILED -ne 0 ]]; then
	echo "Failed Tests:"
	cat tests.txt
fi
```


![image](https://user-images.githubusercontent.com/114262093/204220934-6176b90b-f9c1-46e5-a622-13ea6d25927e.png)

![image](https://user-images.githubusercontent.com/114262093/204223123-1db033bb-27f7-4223-8008-0911b7a41d9e.png)
