Theseus
========
Theseus is an open-source personal tracking tool that uses your iPhone 5S's location and motion sensors to help you track and visualize where you spend your time. It's very similar to [Moves](http://moves-app.com) or [Google Latitude](https://en.wikipedia.org/wiki/Google_Latitude).

One of the key differences between Theseus and other similar apps is its approach to privacy and data accessibility. By default, your data never leaves your phone; all processing happens on-device rather than an external server. If you want to access your data for personal usage, Theseus can export your data to Dropbox in JSON format for easy access.


Installation
------------
Although Theseus will eventually be available on the iOS App Store, you must currently compile it from source.

It currently requires an iPhone 5S, as it makes use of the M7 motion coprocessor.

Assuming you want to run Theseus on your physical iPhone, you will need to be a member of Apple's [iOS Developer Program](https://developer.apple.com/devcenter/ios/index.action).

1. Clone this git repo

`git clone git@github.com:lazerwalker/Theseus.git`

2. Copy `Configuration.plist.example` to `Configuration.plist`.

3. Create a new Foursquare app (https://foursquare.com/developers/register), and a new Dropbox app (https://www.dropbox.com/developers/apps). These will be necessary to fetch Foursquare venues and export your data to Dropbox.

4. Open up `Theseus.xcworkspace` in Xcode. Open `Configuration.plist`, and enter the credentials for the Dropbox and Foursquare apps you created in the previous step.

5. Build and run the app. It should just work!


Issues
------
Theseus is currently early alpha software intended for developers. If you care about losing data, you will want to export your data regularly.

If you run into problems, please file bugs using this repo's [GitHub Issues](https://github.com/lazerwalker/Theseus/issues). If you run into problems with how your movement is being categorized (incorrect timestamps, coordinates, etc) and feel comfortable sharing your data, you can get a raw export of your movement and motion data by choosing the "Export Raw Data" option from the app's settings page; this will be very helpful.


Running Tests from the Command Line
-----------------------------------
You can run Theseus's test suite from the command line by running the `rake test` command from inside the root project directory.

As a warning: the test suite *will* overwrite the app's database in the simulator with test data. It's unlikely you will have meaningful data stored in your simulator instance of the app, but keep this in mind.

Right now, test coverage is a bit shaky; this is a relatively high near-term priority.

Contributing
------------
Contributions of all shapes and forms are welcome! If you're looking for something to do, check out the [GitHub Issues] issue tracker or feel free to get in touch directly.

Before your first pull request is accepted, you will need to submit a Contributor License Agreement by filling out this form: [Theseus CLA](https://docs.google.com/forms/d/1aQZYW0zHQYSrKaFlCgZUnRvwz0gy-ZIgokbMKLOFL5M/viewform). Without a signed CLA, I won't be able to include your code in any builds I submit to Apple for distribution on the App Store.

### Info.plist
Using the Dropbox API requires the app to register a URI scheme of the form "db-<APP KEY>". This automated as part of the build process; whatever app key you have in your Configuration.plist file will be used. Unfortunately, this means it will show up as part of your git changeset. Since gitignoring Info.plist would have other consequences, and we can't selectively gitignore that part of it, for now you'll have to manually discard it from your working index when you commit. Please try to remember to do this, but don't freak out if you accidentally do commit it; a Dropbox app key isn't considered sensitive information, so it isn't the end of the world.

Contact
-------
Mike Lazer-Walker

- https://github.com/lazerwalker
- [@lazerwalker](http://twitter.com/lazerwalker)
- http://lazerwalker.com


License
-------
Theseus is available under the GPL v2 license. See the LICENSE file for more info.