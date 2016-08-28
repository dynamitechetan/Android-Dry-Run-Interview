# Android-Dry-Run-Interview

This is a “dry-run” interview that simulates an in-person interview. The "dry-run" interview will consist of a series of questions that should be answered within a 1 hour time limit. One may add images where applicable to simulate any "whiteboard" drawings.


####**Questions (6 total)**

For each of the questions below, answer as if you were in an interview, explaining and justifying your answer with two to three paragraphs as you see fit. For coding answers, explain the relevant choices you made writing the code.

## Question 1 - What’s your favorite tool or library for Android? Why is it so useful?
> My favourite tool in android is Gradle. Gradle build scripts tend to be much shorter and clearer than those written for Ant or Maven. The amount of boilerplate code is much smaller with Gradle since its DSL is designed to solve a specific problem.

## Question 2 - You want to open a map app from an app that you’re building. The address, city, state, and ZIP code are provided by the user. What steps are involved in sending that data to a map app?

1. Get the full address from the user.
2. Then I will build a uri to pass it to the maps app.<br>
  String uri =  geo:0,0?q=my+street+address;
3. Then use the uri to create a Intent and Launch the maps activity
```java
  Intent intent = new Intent(android.content.Intent.ACTION_VIEW, Uri.parse(uri));
  intent.setClassName("com.google.android.apps.maps", "com.google.android.maps.MapsActivity");
  startActivity(intent);
  ```

## Question 3 - Implement a method to perform basic string compression using the counts of repeated characters. For example, the string aabcccccaaa would become a2b1c5a3. If the "compressed" string would not become smaller than the original string, your method should return the original string. The method signature is: “public static String compress(String input)” You must write all code in proper Java, and please include import statements for any libraries you use.

```java
public class StringCompression {
    
private static String compress(String str) {

    if (str == null) {

        return null;

    } else if (str.length() <= 2) {

        return str;

    }


    StringBuilder stringBuilder = new StringBuilder();
    char temp = str.charAt(0);
    int count = 1;
    for (int i = 1; i < str.length(); i++) {
        if (temp == str.charAt(i)) {
            count++;
        } else {
            stringBuilder.append(temp);
            stringBuilder.append(count);
            temp = str.charAt(i);
            count = 1;
            if (stringBuilder.length() >= str.length()) {
                return str;
            }
        }
    }
    stringBuilder.append(temp).append(count);

    if (stringBuilder.length() >= str.length()) {
        return str;
    } else {
        return stringBuilder.toString();
    }
}

public static void main(String z[]){
System.out.println(compress("aaaaaaabbbbba"));
}

}
```

## Question 4 - List and explain the differences between four different options you have for saving data while making an Android app. Pick one, and explain (without code) how you would implement it.
> Options to store data: 1. Shared preferences 2. SQLite database 3. Files 4. External storage / Online / APIs;
	Shared Preferences are the easiest way for persistent data storage. It is based on key-value pair storage. Data remains on device even after reboots and is removed if data is cleared by user from the settings or the app is uninstalled.<br>
	
> To write values:
    1. Call edit() to get a SharedPreferences.Editor.<br>
    2. Add values with methods such as putBoolean() and putString().<br>
    3. Commit the new values with commit().<br>
  But this method is not so effective for large datasets.<br>
  

## Question 5 - What are your thoughts about Fragments? Do you like or hate them? Why?
> Fragments are a powerful feature of the Android platform and are slightly complex.
The main reason to use Fragments are for the backstack and lifecycle features. It makes it easy to reuse our views.
I am in favour of using Fragments as they provide various advantages and helps in making great UI/UX/
In the case of tablets, we can use a single activity and attach two fragments to it, one for showing the list and the other for the detail.

## Q6: If you were to start your Android position today, what would be your goals a year from now? 
> By next year, I want to see myself leading a team or android developers, building something great.
