# Part 1:

Task: In DocSearchServer.java, add a new line right before File[] paths = f.listFiles(); that prints out the toString of f and a message saying it’s a directory.

```
/
File[]
<enter>
```
![image](https://user-images.githubusercontent.com/114262093/205028448-7c47573e-29fe-4178-b36c-46ab2a91c0a1.png)

```
i
System.out.println(f.toString() + " is a directory");
<enter>
<esc>
```
![image](https://user-images.githubusercontent.com/114262093/205028747-dd14572c-5bb5-4660-a335-476312e1d1f4.png)

```
<esc>
:wq
```

# Part 2:

Editing the code through visual studio code took 123 seconds. Making the edit through vim took 257 seconds.

I probably could have done it through vscode faster, however logging in to ssh and running the program took longer than expected due to me not remembering the commands. Vim took longer because I had to remember the key presses to use, so I had to switch between tabs a lot.

I much prefer using vscode as I am more familiar with that way of editing. It is the standard for all text editors and will autofill code. Its only annoying to have to scp the code every time I make an edit. Vim is completely new to me so I don't have all the commands memorized.

I think the convinience of being able to directly edit on the ssh server will factor into my decision once I get good at using vim. If I know all the commands in muscle memory, my workflow would be much faster.
