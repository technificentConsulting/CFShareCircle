#CFShareCircle

CFShareCircle is a better way for app developers to let users share the content to many different services. It is a simple UIView that adds drag and share capabilities to a developers application. View was only tested on iOS 6.0, but should be 5.1+ capable.

![Demo Image](http://i.imgur.com/9qd0V.png?1)

##How To Use

Follow the instructions to add CFShareCircle to your project.

###Basic Setup

1. Add the following frameworks to your project under "Link Binary With Libraries" in "Build Phases"
    - UIKit
    - QuartzCore
    - Foundation
    - CoreGraphics

2. Add the images directory and CFShareCircle resources to your project. Make sure that the CFShareCircle.m and CFShareCircle.h are listed under "Copy Bundle Resources" under "Build Phases".

3. Edit your view controller header file to import the CFShareCircle header file, add the delegate, and create an object.

    ```
    #import "CFShareCircleView.h"
    
    @interface ViewController : UIViewController <CFShareCircleViewDelegate>{    
        CFShareCircleView *shareCircleView;        
    }
      ```
      
4. In your viewDidLoad method instantiate the CFShareCircle, set up the delegate, and add it to your navigation controller.
```
- (void)viewDidLoad
{
        [super viewDidLoad];
        // Do any additional setup after loading the view, typically from a nib.
        shareCircleView = [[CFShareCircleView alloc] init];
        shareCircleView.delegate = self;
        [self.navigationController.view addSubview:shareCircleView];
}
```

5. Implement both of the delegate methods for the view. Note: Index returned from the view is in order of the array (i.e. Starts from pi = 0 on the unit circle).
``` 
    - (void)shareCircleView:(CFShareCircleView *)aShareCircleView didSelectIndex:(int)index{
        NSLog(@"Selected index: %d", index);
        [shareCircleView animateOut];
    }

    - (void)shareCircleViewWasCanceled{
        [shareCircleView animateOut];
    }
```

6. Finally just animate in the view whenever you want it to present to the user.
```
    [shareCircleView animateIn];
```

###Custom Sharing Images

To customize what sharing images you want to show all you have to do is intialize with your own array of images.

```
shareCircleView = [[CFShareCircleView alloc] initWithImageFileNames:[[NSArray alloc] initWithObjects: @"facebook.png", @"twitter.png", @"email.png", nil]];
```

List of sharing icons included with project.

    - Evernote (evernote.png)
    - Twitter (twitter.png)
    - Google+ (googleplus.png)
    - Facebook (facebook.png)
    - Email (email.png)
    - Message (message.png)
    
##Contact
[Twitter](https://twitter.com/camdenfullmer)

[Website](https://camdenfullmer.com)
    
##License
The MIT License (MIT)
Copyright (c) 2013 Camden Fullmer

Permission is hereby granted, free of charge, to any person obtaining a copy of this software and associated documentation files (the "Software"), to deal in the Software without restriction, including without limitation the rights to use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies of the Software, and to permit persons to whom the Software is furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.
