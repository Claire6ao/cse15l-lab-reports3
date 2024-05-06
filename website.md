<h1>Lab Report 3</h1>

<h2>Part one</h2>

The input that induces failures :
```
public class ArrayTests {
	@Test 
	public void testReverseFail() {
    		int[] input1 = {1,2,3};
    		ArrayExamples.reverseInPlace(input1);
    		assertArrayEquals(new int[]{3,2,1}, input1);
	}
}
```

The input does not induce failure:

```
public class ArrayTests {
@Test
	public void testReversedPass() {
    		int[] input2 = {0};
    		assertArrayEquals(new int[]{0}, ArrayExamples.reversed(input2));
  	}
}
```

The symptop: 
![Updated Image](terminal.png)

Bug:
```
static int[] reversed(int[] arr) {
    int[] newArray = new int[arr.length];
    for(int i = 0; i < arr.length; i += 1) {
      arr[i] = newArray[arr.length - i - 1];
    }
    return arr;
  }
```

Debug:
```
static int[] reversed(int[] arr) {
    int[] newArray = new int[arr.length];
    for(int i = 0; i < arr.length; i += 1) {
      newArray[i] = arr[arr.length - i - 1];
    }
    return newArray;
  }
```
In the previous code, it creates a new array, but assigning the values in the new array to arr and return it. Since the new array is empty, the return value would also be empty, so it would not work. In my fixing, I instead assign the values of the input array reversely to the new array and return the new array. 

<h2>Part two</h2>

command `find`: </n>
the basic syntax is `find [location] [option] [search term]` 
</n>

Option 1: `-name` 
<br>
this is used to find the files with its name containing the search term.

```
clairegao@Claires-MacBook-Pro ~ % find ./Downloads -name "cse12"
clairegao@Claires-MacBook-Pro ~ % find ./Downloads -name "cse12-sp24-pa5-HashTable-starter-main"
./Downloads/cse12-sp24-pa5-HashTable-starter-main
```
<br>
<br>
  
Option 2: `-type`
 <br>

this is used to find the files with the specified type

for example, this command finds the directory in chat-server 
```
clairegao@Claires-MacBook-Pro ~ % find ./chat-server -type d 
./chat-server
./chat-server/chathistory
./chat-server/lib
./chat-server/.git
./chat-server/.git/objects
./chat-server/.git/objects/pack
./chat-server/.git/objects/info
./chat-server/.git/info
./chat-server/.git/logs
./chat-server/.git/logs/refs
./chat-server/.git/logs/refs/heads
./chat-server/.git/logs/refs/remotes
./chat-server/.git/logs/refs/remotes/origin
./chat-server/.git/hooks
./chat-server/.git/refs
./chat-server/.git/refs/heads
./chat-server/.git/refs/tags
./chat-server/.git/refs/remotes
./chat-server/.git/refs/remotes/origin
```

the command finds the file with the name "update.sample" in chat-server
```
clairegao@Claires-MacBook-Pro ~ % find ./chat-server -type f -name "update.sample" 
./chat-server/.git/hooks/update.sample
```
 <br>
<br>
Option 3: `-atime`
 <br>

this commands find the files that has been accessed with the given amount of period

for example, this command find files in desktop that was last accessed more than 1 day ago.
```
clairegao@Claires-MacBook-Pro ~ % find ./Desktop -atime +1
./Desktop/.DS_Store
./Desktop/code2.png
./Desktop/ls.png
./Desktop/.localized
./Desktop/code1.png
./Desktop/final schedule.pdf
./Desktop/Screenshot 2024-04-25 at 12.06.41 PM.png
./Desktop/Screenshot 2024-04-11 at 5.23.56 PM.png
./Desktop/Screenshot 2024-04-25 at 12.22.04 PM.png
./Desktop/add-message1.png
./Desktop/Screenshot 2024-04-18 at 12.18.09 PM.png
./Desktop/Screenshot 2024-04-30 at 4.27.21 PM.png
./Desktop/Double-Major-Petition.pdf
./Desktop/transfer.pages
./Desktop/Screenshot 2024-04-11 at 5.25.31 PM.png
./Desktop/Screenshot 2024-04-25 at 12.12.31 PM.png
./Desktop/Screenshot 2024-04-11 at 5.05.37 PM.png
./Desktop/Screenshot 2024-04-05 at 4.45.33 PM.png
./Desktop/Screenshot 2024-04-25 at 12.14.09 PM.png
./Desktop/loggin.png
./Desktop/add-m2.png
./Desktop/webregMain.pdf
./Desktop/BIPN194 .pages
```

this command find files in desktop that was last accessed less than 1 day ago.
```
clairegao@Claires-MacBook-Pro ~ % find ./Desktop -atime -1
./Desktop
./Desktop/Screenshot 2024-05-06 at 11.50.43 AM.png
```
 <br>
  <br>
  
Option 4: `maxdepth`
<br>
this is command find files but limit subdirectory traversal to 2 levels beneath the given directory.</n>

For example, this command find files containing pdf, but limit subdirectory traversal to 1 level beneath download directory. 
```
clairegao@Claires-MacBook-Pro ~ % find ./Downloads -maxdepth 1 -name '*.pdf' 
./Downloads/26a12f4e-53bf-4535-8aec-d762d5206f4e.pdf
./Downloads/线上见面会 - Google Docs.pdf
./Downloads/CSE15L-W24-Lecture01.pptx.pdf
./Downloads/graphtheory textbook.pdf
./Downloads/cse15l-lab-report2.pdf
./Downloads/transgene.pdf
./Downloads/cse15l-lab-reports1.pdf
./Downloads/Resume.pdf
./Downloads/academichistoryreviewpdf.pdf
./Downloads/Lecture 16 Feb 16.pdf
./Downloads/Photo.pdf
./Downloads/prophets-of-the-hood-politics-and-poetics-in-hip-hop-9780822386155_compress.pdf
./Downloads/Discussion9.pdf
./Downloads/Computer simulations predict the impact of neuronal atrophy on the calcium dynamics in Huntington's disease 2023-4649.pdf
```

this command find files containing pdf, but limit subdirectory traversal to 2 levels beneath download directory
```
clairegao@Claires-MacBook-Pro ~ % find ./Downloads -maxdepth 2 -name '*.pdf'
./Downloads/26a12f4e-53bf-4535-8aec-d762d5206f4e.pdf
./Downloads/线上见面会 - Google Docs.pdf
./Downloads/CSE15L-W24-Lecture01.pptx.pdf
./Downloads/computional brain/1 introductin.pdf
./Downloads/computional brain/3 computational overview.pdf
./Downloads/computional brain/2 neuroscience overview.pdf
./Downloads/graphtheory textbook.pdf
./Downloads/cse15l-lab-report2.pdf
./Downloads/transgene.pdf
./Downloads/cse15l-lab-reports1.pdf
./Downloads/Resume.pdf
./Downloads/academichistoryreviewpdf.pdf
./Downloads/Lecture 16 Feb 16.pdf
./Downloads/Photo.pdf
./Downloads/Hum4/SieyesThirdEstate.pdf
./Downloads/Hum4/Lessing-Education.pdf
./Downloads/Hum4/kant gw2.pdf
./Downloads/Hum4/French rev Sieyes.pdf
./Downloads/Hum4/Second Treatise Of Government, by John Locke.pdf
./Downloads/Hum4/Schiller.pdf
./Downloads/Hum4/kant grwk1.pdf
./Downloads/Hum4/rousseau.pdf
./Downloads/Hum4/Kant-Enlightenment.pdf
./Downloads/Hum4/Schleiermacher1-2.pdf
./Downloads/Hum4/summary.pdf
./Downloads/Hum4/Immanuel_Kant_Groundwork_for_the_Metaphysics_of_Morals_1785.pdf
./Downloads/Hum4/Rousseau_-_Jean-Jacques_Rousseau.pdf
./Downloads/Hum4/Hum4-Syllabus%28S2023%29.pdf
./Downloads/Hum4/novalis.pdf
./Downloads/cse11-pa1-starter-main/Instructions for setting up Java on your own machine.pdf
./Downloads/mus17/2024mus17week3.pdf
./Downloads/mus17/2024mus17week2.pdf
./Downloads/mus17/2024mus17week1.pdf
./Downloads/prophets-of-the-hood-politics-and-poetics-in-hip-hop-9780822386155_compress.pdf
./Downloads/Discussion9.pdf
./Downloads/Computer simulations predict the impact of neuronal atrophy on the calcium dynamics in Huntington's disease 2023-4649.pdf
```

source: 
1. https://snapshooter.com/learn/linux/find#basic-syntax
2. https://www.computerhope.com/unix/ufind.htm#examples

