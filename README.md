# PaperTrailLumberjack
PaperTrailLumberjack is a CocoaLumberjack logger that helps log statements to your log destination at [papertrailapp](http://papertrailapp.com).
It can log using TCP and UDP. On OS X, TLS is supported on TCP Connections, while, on iOS, TCP connections are currently only plain-text.
The default is UDP (which is always unencrypted).

## Usage Swift

To run the example project; clone the repo, and run `pod install` from the Example directory first.

Example UDP logging:

    let paperTrailLogger = RMPaperTrailLogger.sharedInstance()
    paperTrailLogger?.host = "logsXX.papertrailapp.com"
    paperTrailLogger?.port = 1234567
    paperTrailLogger?.debug = false
    DDLog.add(paperTrailLogger!)
    DDLogVerbose(@"Hi PaperTrailApp.com");

Your log messages are automatically formatted to meet the syslog specs, which, typically haves a machine name and program name pre-fixed to the log, along with a timestamp. In order to maintain user privacy, PaperTrailLumberjack uses a unique UUID per device (the UUID is random and reset each time the application is deleted and installed again). The program name is the bundle name stripped of whitespaces.

Sample log output:

    May 08 23:20:59 0A3F9C64-D271-452F-AD6E-8052BBD3F789 PaperTrailLumberjackiOSExample: 60b PaperTrailLumberjackiOSExampleTests@testUdpLogging@62 "Hi PaperTrailApp.com"

## Installation

PaperTrailLumberjack is available through [CocoaPods](http://cocoapods.org), to install
it simply add the following line to your Podfile:

    pod 'PaperTrailLumberjack', :git => 'https://github.com/moflo/papertrail-lumberjack-ios.git'

## Author

George Malayil-Philip, [george.malayil@roguemonkey.in](mailto:george.malayil@roguemonkey.in)

[Rogue Monkey Technologies & Systems Private Limited](http://www.roguemonkey.in)

## License

PaperTrailLumberjack is available under the MIT license. See the LICENSE file for more info.
