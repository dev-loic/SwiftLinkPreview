# Swift Link Preview

It makes a preview from an url, grabbing all the information such as title, relevant texts and images.

[![Platform](https://img.shields.io/badge/platform-iOS-red.svg)](https://github.com/LeonardoCardoso/SwiftLinkPreview#requirements-and-details)
[![CocoaPods](https://img.shields.io/badge/pod-v0.0.3-blue.svg)](https://github.com/LeonardoCardoso/SwiftLinkPreview#cocoapods)
[![Carthage Compatible](https://img.shields.io/badge/Carthage-compatible-4BC51D.svg)](https://github.com/LeonardoCardoso/SwiftLinkPreview#carthage)

#### Index 

* [Visual Examples](#visual-examples)
* [Requirements and Details](#requirements-and-details)
* [Installation](#installation)
	* [CocoaPods](#cocoapods)
	* [Carthage](#carthage)
	* [Manually](#manually)
* [Usage](#usage)
	* [Instatiating](#instatiating)
	* [Requesting preview](#requesting-preview)
	* [Cancelling a request](#cancelling-a-request)
* [Flow](#flow)
* [Important](#important)
* [Tips](#tips)
* [Information and Contact](#information-and-contact)
* [Related Projects](#related-projects)
* [License](#license)

## Visual Examples

**UTF-8** | **Extended UTF-8**	 | **Gallery** 
:--:|:--:|:--:|	
![UTF-8](Images/default.gif "UTF-8") | ![Extended UTF-8](Images/langs.gif "Extended UTF-8") |![Gallery](Images/gallery.gif "Gallery")
**Video Websites** | **Images** 
![Video Websites](Images/videos.gif "Video Websites") | ![Images](Images/images.gif "Images") | 

## Requirements and Details

* iOS 8.0+
* Xcode 7.3+
* Built with Swift 2.2

## Installation

### CocoaPods

```ruby
	source 'https://github.com/CocoaPods/Specs.git'
	platform :ios, '8.0'
	
	target 'Your Target Name' do
	  	use_frameworks!
	  	// ...
	  	pod 'SwiftLinkPreview', '~> 0.0.3'
	  	// ...
	end
```

### Carthage

```ruby
  	// ...
	github "LeonardoCardoso/SwiftLinkPreview" ~> 0.0.3
  	// ...
```

### Manually

You just need to drop SwiftLinkPreview folder into Xcode project (make sure to enable "Copy items if needed" and "Create groups").


## Usage

#### Instatiating
```swift
import SwiftLinkPreview

// ...

let slp = SwiftLinkPreview()
```

#### Requesting preview
```swift
slp.preview(
    "Text containing url",
    onSuccess: { result in
    	
		print("\(result)")
        
    },
    onError: { error in
       
		print("\(error)")
        
    }
)
```
**result** is a dictionary ```[String: AnyObject]``` like:

```swift
[
   "url": "original URL", 								// NSURL
   "finalUrl": "final ~unshortened~ URL.", 				// NSURL
   "canonicalUrl": "canonical URL", 					// NSURL
   "title": "title", 									// String
   "description": "page description or relevant text", 	// String
   "images": ["array of URLs of the images"], 			// String array
   "image": "main image" 								// String
]
```

#### Cancelling a request
```swift
slp.cancel()
```

# FLOW

![flow](http://i.imgur.com/SMueQkA.png)

## Important

You need to set ```Allow Arbitrary Loads``` to ```YES``` on your project's Info.plist file.

![app security](http://i.imgur.com/41hGjCC.png)

If you don't want to use the option above and you are using ```SwiftLinkPreview``` for services of your knowledge, you can whitelist them on Info.plist file as well. You can read more about it [here](http://stackoverflow.com/questions/30739473/nsurlsession-nsurlconnection-http-load-failed-on-ios-9), [here](https://github.com/Alamofire/Alamofire#app-transport-security) and [here](https://ste.vn/2015/06/10/configuring-app-transport-security-ios-9-osx-10-11/).

![app security](http://i.imgur.com/INEp6q5.png)

## TIPS

Not all websites will have their info brought, you can treat the info that your implementation gets as you like. But here are two tips about posting a preview:

* If some info is missing, you can offer the user to enter it. Take for example the description.
* If more than one image is fetched, you can offer the user the feature of picking one image.

## Information and Contact

Developed by [@LeonardoCardoso](https://github.com/LeonardoCardoso). 

For more information, please visit [http://ios.leocardz.com/swift-link-preview/](http://ios.leocardz.com/swift-link-preview/).

Contact me either by Twitter [@leocardz](https://twitter.com/leocardz) or emailing me to [contact@leocardz.com](mailto:contact@leocardz.com).

## Related Projects

* [Link Preview (PHP + Angular + Bootstrap)](https://github.com/LeonardoCardoso/Link-Preview)
* [Android Link Preview](https://github.com/LeonardoCardoso/Android-Link-Preview)


## License

    The MIT License (MIT)

	Copyright (c) 2016 Leonardo Cardoso
	
	Permission is hereby granted, free of charge, to any person obtaining a copy
	of this software and associated documentation files (the "Software"), to deal
	in the Software without restriction, including without limitation the rights
	to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
	copies of the Software, and to permit persons to whom the Software is
	furnished to do so, subject to the following conditions:
	
	The above copyright notice and this permission notice shall be included in all
	copies or substantial portions of the Software.
	
	THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
	IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
	FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
	AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
	LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
	OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
	SOFTWARE.