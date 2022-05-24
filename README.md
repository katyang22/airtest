# airtest
set up:

1.Download IDE from link:https://airtest.netease.com/index.html.

For android devices:
2.connect to android devices using USB.


3. remote connection:enter remote IP address to connect with remote devices.


<img width="339" alt="Screen Shot 2022-05-24 at 2 18 35 PM" src="https://user-images.githubusercontent.com/97198638/170134440-a1e329ca-3faa-4d74-8d17-47803b1b71c3.png">

For iOS devices:

1.1 Clone or Download iOS-Tagent

git clone git@github.com:AirtestProject/iOS-Tagent.git
1.2 Open iOS-Tagent with Xcode and connect your iPhone to Mac with a data cable

Select product -> Scheme -> WebDriverAgentRunner in the top menu of Xcode
Then select product -> Destination -> your iPhone
chooseScheme

1.3 Start tests by click product -> Test. When something like this shows in the log, it means that iOS-Tagent have started successfully.

    Test Suite 'All tests' started at 2017-01-23 15:49:12.585
    Test Suite 'WebDriverAgentRunner.xctest' started at 2017-01-23 15:49:12.586
    Test Suite 'UITestingUITests' started at 2017-01-23 15:49:12.587
    Test Case '-[UITestingUITests testRunner]' started.
    t =     0.00s     Start Test at 2017-01-23 15:49:12.588
    t =     0.00s     Set Up
More about how to start WebDriverAgent here and here

2. Set up proxy

iproxy maps the iPhone port to the Mac port, so you can access the phone by accessing the Mac.

You need to set up the usb proxy to access the Agent on the actual phone, as there may be problems when accessing directly through wifi. For more information, check Issues and detail

The original source code of iproxy is shown in https://github.com/libimobiledevice/libimobiledevice

2.1 Install iproxy with Homebrew

$ brew install libimobiledevice

2.2 Run iproxy

$ iproxy 8100 8100

Then try to access http://127.0.0.1:8100/status in your mac browser. If a json data about your iPhone is returned, it means iproxy started successfully. Moreover, you can see iPhone screen projected on the browser by visiting http://127.0.0.1:8100/inspector .

Note that iproxy can only listen to localhost. If you want to connect iPhone on AirtestIDE on a windows OS, you can try wdaproxy. The specific steps are as follows:

Connect iPhone to Mac with a usb cable.
Run wdaproxy in Mac. wdaproxy can map the iPhone port to the Mac port too. You can see the installation instruction in https://github.com/openatx/wdaproxy .
Fill ip address and port of the iPhone (retrieved in the previous step) in the input box of AirtestIDE on Windows and click button "connect".
3. AirtestIDE

Connect to the iPhone by ip address, refresh screen, run tests

After the above two steps, you can fill "http://127.0.0.1:8100" in the iOS address input box of AirtestIDE. Click button "connect" to connect your iPhone and start your Airtest test.

connectDevice

 image
