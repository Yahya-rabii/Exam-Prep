# Flutter Exam Revision:


## The main elements of the flutter app:


- how to create a new flutter project using the terminal

```bash

flutter create <project name>

```

- exlain each of the folders in the project
    
    - android - contains the android project files
    - ios - contains the ios project files
    - lib - contains the dart files
    - test - contains the test files
    - web - contains the web project files
    - .gitignore - contains the files that git should ignore
    - .metadata - contains the metadata for the project
    - .packages - contains the packages for the project
    - .flutter - contains the flutter project files
    - pubspec.lock - contains the packages for the project
    - pubspec.yaml - contains the packages for the project





- explain the difference between stateless and stateful widgets
    - stateless widgets are widgets that do not change over time


```dart

// stateless widget

class StatelessWidget extends StatelessWidget {
  const StatelessWidget({Key? key}) : super(key: key);

  @override
  Widget build(BuildContext context) {
    return Container();
  }
}
```
- 
    - stateful widgets are widgets that can change over time

```dart
// stateful widget

class StatefulWidget extends StatefulWidget {
  const StatefulWidget({Key? key}) : super(key: key);

  @override
  State<StatefulWidget> createState() {
    return _StatefulWidgetState();
  }
}

class _StatefulWidgetState extends State<StatefulWidget> {
  @override
  Widget build(BuildContext context) {
    return Container();
  }
}

```


- the main elements of the flutter app

```dart


// imports example:

import 'package:allen/feature_box.dart';  // Import the FeatureBox widget
import 'package:allen/pallete.dart';  // Import the Pallete class
import 'package:allen/ChatgptInterface.dart';  // Import the ChatgptInterface widget
import 'package:allen/DalleInterface.dart';  // Import the DalleInterface widget
import 'package:animate_do/animate_do.dart';  // Import animations from the animate_do package
import 'package:flutter/material.dart';  // Import the Flutter material library


// home page class example: 

class HomePage extends StatefulWidget {
  /*
  the home page class is the root widget of the app
  */
  const HomePage({Key? key}) : super(key: key); // Constructor for the home page class


// home page state class example:

  @override
  State<HomePage> createState() => _HomePageState(); // Create a state for the home page class

/* 
  the home page state class is the home widget of the app
  it takes no arguments
  it returns a stateful widget that returns a scaffold which contains a center widget that contains a text widget
*/

}

class _HomePageState extends State<HomePage> {

/*

_HomePageState class is the state of the home page class it means that it can change over time 

*/


  int atribut = 0; // atribut variable

  void _onItemTapped(int index) {
    setState(() {
      _selectedIndex = index;  
    });

    // Navigate to the selected screen
    if (index == 0) {
      Navigator.push(
        context,
        MaterialPageRoute(builder: (context) => ChatgptInterface()),  // Navigate to ChatGPT interface
      );
    } else if (index == 1) {
      Navigator.push(
        context,
        MaterialPageRoute(builder: (context) => DalleInterface()),  // Navigate to DALL-E interface
      );
    }
  }


  /*
    the _onItemTapped function is a function that takes an index and returns nothing
    it sets the selected index to the index that was passed to it
    it then navigates to the selected screen
    */

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(
        title: BounceInDown(
          child: const Text("Hey there! welcome to "),  // Title of the app bar with bounce animation
        ),
        centerTitle: true,  // Center align the title
      ),
      bottomNavigationBar: BottomNavigationBar(
        items:  <BottomNavigationBarItem>[
          BottomNavigationBarItem(
            icon: Image.asset(
              'assets/images/chatgpt.png',  // ChatGPT logo
              width: 24,
              height: 24,
            ),
            label: 'ChatGPT',  // Label for ChatGPT bottom nav item
          ),
          BottomNavigationBarItem(
            icon: Image.asset(
              'assets/images/dalle.png',  // DALL-E logo
              width: 24,
              height: 24,
            ),
            label: 'DALL-E',  // Label for DALL-E bottom nav item
          ),
        ],
        currentIndex: _selectedIndex,  // Current selected index
        onTap: _onItemTapped,  // Function to call when an item is tapped
      ),
      body: SingleChildScrollView(
        child: Column(
          children: [
            // Virtual assistant picture with zoom in animation
            ZoomIn(
              child: Stack(
                children: [
                  Center(
                    child: Container(
                      height: 120,
                      width: 120,
                      margin: const EdgeInsets.only(top: 4),
                      decoration: const BoxDecoration(
                        color: Pallete.assistantCircleColor,  // Assistant circle color
                        shape: BoxShape.circle,
                      ),
                    ),
                  ),
                  Container(
                    height: 123,
                    decoration: const BoxDecoration(
                      shape: BoxShape.circle,
                      image: DecorationImage(
                        image: AssetImage(
                          'assets/images/ai.png',  // Assistant image
                        ),
                      ),
                    ),
                  ),
                ],
              ),
            ),
            // Chat bubble with fade in animation
            FadeInRight(
              child: Visibility(
                child: Container(
                  padding: const EdgeInsets.symmetric(
                    horizontal: 20,
                    vertical: 10,
                  ),
                  margin: const EdgeInsets.symmetric(horizontal: 40).copyWith(
                    top: 30,
                  ),
                  decoration: BoxDecoration(
                    border: Border.all(
                      color: Pallete.borderColor,  // Border color
                    ),
                    borderRadius: BorderRadius.circular(20).copyWith(
                      topLeft: Radius.zero,
                    ),
                  ),
                  child: const Padding(
                    padding: EdgeInsets.symmetric(vertical: 10.0),
                    child: Text(
                      "Hello, how can I assist you today?",  // Initial chat message
                      style: TextStyle(
                        fontFamily: 'Cera Pro',
                        color: Pallete.mainFontColor,  // Font color
                        fontSize: 18,
                      ),
                    ),
                  ),
                ),
              ),
            ),

            SlideInLeft(
              child: Visibility(
                child: Container(
                  padding: const EdgeInsets.all(10),
                  alignment: Alignment.centerLeft,
                  margin: const EdgeInsets.only(top: 10, left: 22),
                  child: const Text(
                    'Here are some features.',  // Feature list header
                    style: TextStyle(
                      fontFamily: 'Cera Pro',
                      color: Pallete.mainFontColor,  // Font color
                      fontSize: 20,
                      fontWeight: FontWeight.bold,
                    ),
                  ),
                ),
              ),
            ),
            // Features list with slide in left animation
            Visibility(
              child: Column(
                children: [
                  SlideInLeft(
                    delay: Duration(milliseconds: start),
                    child: const FeatureBox(
                      color: Pallete.firstSuggestionBoxColor,  // Box color for ChatGPT feature
                      headerText: 'ChatGPT',  // Header for ChatGPT feature
                      descriptionText:
                      'A smarter way to stay organized and informed with ChatGPT.',  // Description for ChatGPT feature
                    ),
                  ),
                  SlideInLeft(
                    delay: Duration(milliseconds: start + delay),
                    child: const FeatureBox(
                      color: Pallete.secondSuggestionBoxColor,  // Box color for DALL-E feature
                      headerText: 'DALL-E',  // Header for DALL-E feature
                      descriptionText:
                      'Find inspiration and stay creative with your personal assistant powered by DALL-E.',  // Description for DALL-E feature
                    ),
                  ),
                  SlideInLeft(
                    delay: Duration(milliseconds: start + 2 * delay),
                    child: const FeatureBox(
                      color: Pallete.thirdSuggestionBoxColor,  // Box color for voice assistant feature
                      headerText: 'Intelligent Voice Assistant',  // Header for voice assistant feature
                      descriptionText:
                      'Enjoy the best of both worlds with a voice assistant powered by DALL-E and ChatGPT.',  // Description for voice assistant feature
                    ),
                  ),
                ],
              ),
            )
          ],
        ),
      ),
    );
  }

/* the build function is a function that takes a context and returns a scaffold that contains a appbar, a bottom navigation bar and a body
  
the body of the scaffold contains a group of children :


scaffold
    - appbar
    - bottom navigation bar
    - body
        - single child scroll view
        - column
            - zoom in
            - stack
                - center
                - container
                    - assistant circle color
                    - shape
                    - circle
                - container
                - shape
                    - circle
                - image
                    - assistant image
            - fade in right
            - visibility
                - container
                - padding
                    - horizontal
                    - vertical
                - margin
                    - horizontal
                    - top
                - decoration
                    - border
                    - color
                    - border radius
                    - circular
                        - top left
                - padding
                    - vertical
                    - text
                    - initial chat message
                    - style
                        - font family
                        - color
                        - font size
            - slide in left
            - visibility
                - container
                - padding
                    - all
                - alignment
                    - center left
                - margin
                    - top
                    - left
                - text
                    - feature list header
                    - style
                    - font family
                    - color
                    - font size
                    - font weight
            - visibility
            - column
                - slide in left
                - feature box
                    - color
                    - header text
                    - description text
                - slide in left
                - feature box
                    - color
                    - header text
                    - description text
                - slide in left
                - feature box
                    - color
                    - header text
                    - description text
    
    */
    
    }
   
```


the main elements of the flutter app are the imports, the home page class, the home page state class and the build function:

- imports - the imports are the packages that are used in the app

- home page class - the home page class is the root widget of the app

- home page state class - the home page state class is the state of the home page class it means that it can change over time

- build function - the build function is a function that takes a context and returns a scaffold that contains a appbar, a bottom navigation bar and a body




