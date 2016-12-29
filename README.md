# AndroidDryRunInterview
 This repo contains the answer of Android Dry Run Interview under Udacity Android Nanodegree Program


### Question 1 - What’s your favorite tool or library for Android? Why is it so useful?
> Android has lot of good libraries, like retrofit, volley, butterknife and many more. I liked Retrofit, as it converts rest API into interface, making network calls clean as well as robust. Also, it uses Gson by default, so, there is no need to do any custom parsing, allowing us to focus on business logic.

### Question 2 - You want to open a map app from an app that you’re building. The address, city, state, and ZIP code are provided by the user. What steps are involved in sending that data to a map app?

> To open other app from our app requires intent. These are the steps involved:
1. I have to create Map URI, 
2. Then ask intent service to open the URI in the app, which has already registered to open such kind of URI. So, if google maps is installed, it will open the URI in the map, otherwise it will open the URI in the browser.
3. Start the intent.
Here is the sample code:


```java
    String uri = "http://maps.google.co.in/maps?q=" + yourAddress;
    Intent intent = new Intent(Intent.ACTION_VIEW, Uri.parse(uri));
    context.startActivity(intent);
  ```

### Question 3 - Implement a method to perform basic string compression using the counts of repeated characters. For example, the string aabcccccaaa would become a2b1c5a3. If the "compressed" string would not become smaller than the original string, your method should return the original string. The method signature is: “public static String compress(String input)” You must write all code in proper Java, and please include import statements for any libraries you use.
> Here is the solution:
```java
public class StringCompression {    
    public static String compresString(String text) {
        int length = text.length();
        /*
        *  Compression makes sense at length of larger than or equal to 3.
        *  For instance: "aaa" -> "a3"
        */
        if(length > 2) {
            String compressedText = "";	
            char lastChar = text.charAt(0);	
            int charCount = 1;
            for(int i = 1; i < length; i++) {
                if(text.charAt(i) == lastChar) charCount++;	
                else {
                    compressedText += Character.toString(lastChar) + Integer.toString(charCount);
                    lastChar = text.charAt(i);	
                    charCount = 1;
                }
            }	
            compressedText += Character.toString(lastChar) + Integer.toString(charCount);
            if(compressedText.length() < length)
                return compressedText;		
        }		return text;
    }
}
```
Please find the gist (here)[https://gist.github.com/kinshuk4/1a4d64f884b5d51792a992977366e40c].

### Question 4 - List and explain the differences between four different options you have for saving data while making an Android app. Pick one, and explain (without code) how you would implement it.
> Options to store data: 
a)	Shared Preferences
b)	Internal Storage
c)	External Storage
d)	Sqlite database
(For data not saving on phone, we can use external APIs)

Shared preferences are useful for storing the primitive data types like `integer`, `boolean` and also `String`. 
In onCreate() method, we can create the shared preference, and add it to the Shared Preference database. We can add values with methods such as putInt(), putBoolean() and putString(). 
If at any point, we have to change the preference, we just open the Preference Editor using SharedPreferences.Editor, and just start editing it. Also, we can get the instance at any point of time.

For complex data types, we should use remaining methods.
  

### Question 5 - What are your thoughts about Fragments? Do you like or hate them? Why?
> Fragments are a powerful feature of the Android platform and are slightly complex.
It makes it easy to reuse our views, be it tablet or phone. 
I like fragments as they ease out the android development process, taking care of various views we have to support.
In the case of tablets, we can use a single activity and attach two fragments to it, one for showing the list or grid and the other for the detail.

### Q6: If you were to start your Android position today, what would be your goals a year from now? 
> I would like to learn the internals of android libraries and design patterns, and build very robust and cool apps. <br>
  I would also like to contribute to open source being part of great android community.

