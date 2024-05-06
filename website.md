<h1>Lab Report 3</h1>

<h2>Part one</h2>

```
import static org.junit.Assert.*;
import org.junit.*;

public class ArrayTests {
	@Test 
	public void testReverseFail() {
    		int[] input1 = {1,2,3};
    		ArrayExamples.reverseInPlace(input1);
    		assertArrayEquals(new int[]{3,2,1}, input1);
	}

  	@Test
	public void testReversedPass() {
    		int[] input2 = {0};
    		assertArrayEquals(new int[]{0}, ArrayExamples.reversed(input2));
  	}

}
```

The first one induces failures and the second input does not induce failure.

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
