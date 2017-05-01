## Agenda
1. Understand the platform fundamentals
   * Steps of app building
   * Understanding the runtime environment

2. Manage the state of an application
   * Managing app data

3. Debug and test an HTML5-based touch-enabled application
   * Debugging and testing
   * Validating

4. Publish an application to a store

### How to Build an App
Creating an app requires a number of steps, including:
   1. Planning your project
   2. Designing the UI
   3. Updating the app manifest
   4. Writing the code
   5. Building the app
   6. Debugging and testing the app
   7. Packaging the app
      * Packaging and Publishing are synonymous
   8. Validating the app
   9. Deploying

#### The Runtime Environment
* When you launch an app it's considered to be in a **runtime environment (RTE)**
* Windows has WinRT

#### Windows Runtime (WinRT)
* Provides developers with access to a user's device
   * Hardware
   * OS
* It does this through the WinRT and Windows Library for JavaScript APIs
   * An **application programming interface (API)** is a set of guidelines that allow one program to communicate with another

#### The App Container
* When a Web app executes, it does so in a contained environment
   * An app container is a seperate memory space
* Seperates the Web App from the operating system and avoid corruption

#### .NET Framework
* Provides a secure environment for Web apps to run
* The framework users security **transparency** to seperate different kinds of code while running
   * Transparency prevents app code from running with infrastructure code
* **Permission sets** define what application code has access to and ability to do
   * Being able to access different frameworks, hardware, etc

### Managing App Data

#### Accessing a Web Page
* Enter a **uniform resource locator (URL)** into the address bar, the browser sends an **HTTP request** to a Web server for a Web Page
   * **Hypertext Transfport Protocol**
   * HTTP is stateless - will not retain data from session to session
* When we close a Web browser after using an app, data is not saved automatically

#### State Management
* When a user request access to an app, or use a Web Browser, a **state** is created
* There are 3 different types of states:
   * session
   * application
   * persistent
* When a state starts and ends is dependent upon which type of state it is
* **State Management** is the process of maintaining Web page information and data when using pages and apps

#### Different States
* A **session state** is created when you log in to an app
   * It ends when a user ends the session, or logs out of the app
* An **application state** is created when a browser sends a request for a Web page to a web server
   ** Ends when users closers browser
* **Persistent state information** is data that remains for use by an app after a session ends
   * this allows an app to continue its state when a user returns
   * **cookies**

#### Cookies
* Used to work around stateless nature of HTTP and retain data between sessions
* Small files that save information about users that are saved on the user's computer
* Browsers send cookies back to Web servers, that use the files to identify a user and customize their experience

##### Limitations of Cookies
* The use of cookies can present a number of problems:
   * Security risks
   * Performance decreases due to the amount of data sent between computers
* HTML5 utilized Web storage to counter this
   * Two types of Web storage:
      * localStorage
      * sessionStorage

#### localStorage and sessionStorage
* localStorage lets users save larger amounts of persistent data
   * There is no limit to how long data persists
* sessionStorage lets users save session state data
   * It only lasts for the duration of the session
* Both methods allow users to store large amounts of data without slowing down a connection because it is only transferred only on request

#### AppCache for Offline Files
* Data can be stored locally when a user is offline using the **Application Cache** or **AppCache**
* AppCache stores resources, such as HTML, CSS, and JavaScript files, locally on a user's machine
   * Users can access Web pages and apps offline
* Developers can dicate which type of information is stored locally in the **cache manifest file**

### Debugging and Testing
* **Debugging** and **testing** are incredibly important steps
* Debugging is the process of detecting, finding, and correcting errors in logic and syntax
   * **Logic errors** prevent the app from behaving as expected
   * **Syntax errors** are typoes in code which prevent Web apps from running

#### Validating HTML5 Code
* An important aspect of debugging and testing is to validate code to ensure it is properly interpreted by browsers
* We can use a **validator** to test code for inaccuracies and syntax errors
* **W3C** provides a code validation service for all versions of HTML and CSS
   * [W3C Validator](http://validator.w3.org/)

### Packaging Apps
* Packaging an app is the process of preparing an app for installation on different devices or systems
* If you want to package and publish an app, you can use the **Windows App Certification Kit** to test it
   * Provides a report describing any problems
* If there are problems, correct them and test your app again

### Publishing an App
* After you test, debug and validate your code, it will be ready for upload to a marketplace for apps
* If the app was build for Window,s then the marketplace will be the Windows Store
* Before publishing an app to the Windows Store, you must:
   1. Sign up and pay for a developer account
   2. Go through the app submission checklist
   3. Capture screenshots of unique features in your app
   4. Have other users test your app on multiple devices and platforms
   5. Include a privacy statement if your app gathers personal information or copyrighted software