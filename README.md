<div align="center"><img src="https://github.com/aagarwal1012/IntroViews-Flutter/blob/master/display/header.png?raw=true"/></div>
<br/>
<div align="center">
  <a href="https://flutter.io">
    <img src="https://img.shields.io/badge/Platform-Flutter-yellow.svg"
      alt="Platform" />
  </a>
  <a href="https://pub.dev/packages/intro_views_flutter">
    <img src="https://img.shields.io/pub/v/intro_views_flutter.svg"
      alt="Pub Package" />
  </a>
  <img src="https://github.com/aagarwal1012/IntroViews-Flutter/actions/workflows/build.yml/badge.svg"
      alt="Build Status" />
  <img src="https://github.com/aagarwal1012/IntroViews-Flutter/actions/workflows/tests.yml/badge.svg"
      alt="Tests Status" />
    <a href="https://codecov.io/gh/aagarwal1012/IntroViews-Flutter">
    <img src="https://codecov.io/gh/aagarwal1012/IntroViews-Flutter/branch/master/graph/badge.svg"
      alt="Codecov Coverage" />
  </a>
  	<a href="https://opensource.org/licenses/MIT">
    <img src="https://img.shields.io/badge/License-MIT-red.svg"
      alt="License: MIT" />
  </a>
	<a href="https://www.paypal.me/aagarwal1012">
    <img src="https://img.shields.io/badge/Donate-PayPal-green.svg"
      alt="Donate" />
  </a>
</div><br>

IntroViews is inspired by [Paper Onboarding](https://github.com/Ramotion/paper-onboarding-android) and developed with `love` from scratch. Checkout our fully responsive [live example app](https://introviews-flutter.web.app/).

## Table of contents
  * [Features](#features)
  * [Getting Started](#getting-started)
  * [Usage](#usage)
  * [Documentation](#documentaion)  
  	* [PageViewModel Class](#pageViewModel-class)
  	* [IntroViewFlutter Class](#introViewFlutter-class)
  * [Bugs or Requests](#bugs-or-requests)
  * [Donate](#donate)
  * [Contributors](#contributors)
  * [License](#license)

<img src="https://github.com/aagarwal1012/IntroViews-Flutter/blob/master/display/output.gif?raw=true" align = "right" height = "550px">

# Features

- Easy addition of pages.

- Circular page reveal.

- Cool Animations.

- Animation control, if the user stops sliding in the midway.

- Skip button, for skipping the app intro.

- Custom font selection.

- Material Design.

# Getting Started

You should ensure that you add the `intro_views_flutter` as a dependency in your flutter project.

```yaml
dependencies:
  intro_views_flutter: '^3.2.0'
```

You can also reference the git repository directly if you want:

```yaml
dependencies:
  intro_views_flutter:
    git: git://github.com/aagarwal1012/IntroViews-Flutter
```

You should then run `flutter packages get` in your terminal so as to get the package.

# Usage

<img src = "https://github.com/aagarwal1012/IntroViews-Flutter/blob/master/display/page3.png?raw=true" align = "right" height = "450px"/>

- `IntroViewsFlutter` widget require a `list` of `PageViewModel` , and some other parameters. Refer the code below to create a PageViewModel page.

  ```dart
  import 'package:intro_views_flutter/intro_views_flutter.dart';

  ...

  final page = PageViewModel(
      pageColor: const Color(0xFF607D8B),
        iconImageAssetPath: 'assets/taxi-driver.png',
        body: Text(
          'Easy  cab  booking  at  your  doorstep  with  cashless  payment  system',
        ),
        title: Text('Cabs'),
        mainImage: Image.asset(
          'assets/taxi.png',
          height: 285.0,
          width: 285.0,
          alignment: Alignment.center,
        ),
        titleTextStyle: TextStyle(fontFamily: 'MyFont', color: Colors.white),
        bodyTextStyle: TextStyle(fontFamily: 'MyFont', color: Colors.white),
      );
  ```

- Now refer the code below to get the `IntroViewsFlutter` widget.

  ```dart
  final Widget introViews = IntroViewsFlutter(
        page,
        onTapDoneButton: () {
          // Void Callback
        },
        showSkipButton: true,
        pageButtonTextStyles: TextStyle(
            color: Colors.white,
            fontSize: 18.0,
            fontFamily: 'Regular',
          ),
      );
  ```

  For further usage refer the [`example`](https://github.com/aagarwal1012/IntroViews-Flutter/tree/master/example/lib) available.

  For `Landscape` preview click the [link](https://github.com/aagarwal1012/IntroViews-Flutter/blob/master/display/landscape2.png?raw=true).

  **_Note :_** If you added more than four pages in the list then there might be overlapping between `page icons` and `skip button`, so my suggestion is just make the `showSkipButton: false`.

# Documentation

### PageViewModel Class

| Dart attribute        | Datatype       | Description                                                           |                                          Default Value                                          |
| :-------------------- | :------------- | :-------------------------------------------------------------------- | :---------------------------------------------------------------------------------------------: |
| pageColor             | Color?          | Set color of the page.                                                |                                              Null                                               |
| pageBackground        | Widget         | Set a widget as a background of the whole page (pageColor has priority)            |                                              Null                                               |
| mainImage             | Image / Widget | Set the main image of the page. If null, then the widget is omitted. |                                              -                                               |
| title                 | Text / Widget  | Set the title text of the page. If null, then the widget is omitted.                                       |                                              -                                               |
| body                  | Text / Widget  | Set the body text of the page. If null, then the widget is omitted.                                        |                                              -                                               |
| iconImageAssetPath    | String?         | Set the icon image asset path that would be displayed in page bubble. |                                              Null                                               |
| iconColor             | Color?          | Set the page bubble icon color.                                       |                                              Null                                               |
| bubbleBackgroundColor | Color          | Set the page bubble background color.                                 |                                          Colors.white / Color(0x88FFFFFF)                                           |
| textStyle             | TextStyle?      | Set TextStyle for both title and body                                 | title: `color: Colors.white , fontSize: 50.0` <br> body: `color: Colors.white , fontSize: 24.0` |
| titleTextStyle             | TextStyle      | Set TextStyle for title                                 | `color: Colors.white , fontSize: 50.0` |
| bodyTextStyle             | TextStyle      | Set TextStyle for body                                 | `color: Colors.white , fontSize: 24.0` |
| bubble                | Widget?         | Set a custom widget for the inner bubble                              |                                              Null                                               |

### IntroViewFlutter Class

| Dart attribute          | Datatype            | Description                                                                                                       |              Default Value              |
| :---------------------- | :------------------ | :---------------------------------------------------------------------------------------------------------------- | :-------------------------------------: |
| pages                   | List\<PageViewModel\> | Set the pages of the intro screen.                                                                                |                  (required)                   |
| onTapDoneButton         | VoidCallback?        | Method executes on tapping done button.                                                                           |                  Null                   |
| onTapBackButton         | VoidCallback?        | Method executes on tapping back button.                                                                           |                  Null                   |
| onTapNextButton         | VoidCallback?        | Method executes on tapping next button.                                                                           |                  Null                   |
| showSkipButton          | bool                | Show the skip button at the bottom of page.                                                                       |                  true                   |
| showBackButton          | bool                | Show the Back button at the bottom of page. Overrides showSkipButton starting from the second page                |                  false                   |
| showNextButton          | bool                | Show the Next button at the bottom of page. Overrides doneButtonPersist.                                          |                  false                   |
| pageButtonTextSize      | double              | Set the button text size.                                                                                         |                  18.0                   |
| pageButtonFontFamily    | String?              | Set the font of button text.                                                                                      |                 Null                 |
| onTapSkipButton         | VoidCallback?        | Method executes on tapping skip button.                                                                           |                  Null                   |
| pageButtonTextStyles    | TextStyle?           | Configure TextStyle for skip, done buttons, overrides pageButtonFontFamily, pageButtonsColor, pageButtonTextSize. | fontSize: `18.0`, color: `Colors.white` |
| skipText                | Text / Widget       | Override Skip Button Text and styles.                                                                             |              Text('SKIP')               |
| doneText                | Text / Widget       | Override Done Button Text and styles.                                                                             |              Text('DONE')               |
| backText                | Text / Widget       | Override Back Button Text and styles.                                                                             |              Text('BACK')               |
| nextText                | Text / Widget       | Override Next Button Text and styles.                                                                             |              Text('NEXT')               |
| doneButtonPersist       | bool                | Show done Button throughout pages                                                                                 |                  false                  |
| columnMainAxisAlignment | MainAxisAlignment   | Control [MainAxisAlignment] for column                                                                            |      MainAxisAlignment.spaceAround      |
| fullTransition          | double              | Adjust scroll distance for full transition                                                                        |                  300.0                  |
| background              | Color?               | Set the background color to Colors.transparent if you have your own background image below | Null |

For help on editing package code, view the [flutter documentation](https://flutter.io/developing-packages/).

# Bugs or Requests

If you encounter any problems feel free to open an [issue](https://github.com/aagarwal1012/IntroViews-Flutter/issues/new?template=bug_report.md). If you feel the library is missing a feature, please raise a [ticket](https://github.com/aagarwal1012/IntroViews-Flutter/issues/new?template=feature_request.md) on GitHub and I'll look into it. Pull request are also welcome.

See [Contributing.md](https://github.com/aagarwal1012/IntroViews-Flutter/blob/master/CONTRIBUTING.md).

# Donate
> If you found this project helpful or you learned something from the source code and want to thank me, consider buying me a cup of :coffee:
>
> - [PayPal](https://www.paypal.me/aagarwal1012/)

# Contributors

Thanks goes to these wonderful people ([emoji key](https://allcontributors.org/docs/en/emoji-key)):

<!-- ALL-CONTRIBUTORS-LIST:START - Do not remove or modify this section -->
<!-- prettier-ignore-start -->
<!-- markdownlint-disable -->
<table>
  <tr>
    <td align="center"><a href="https://github.com/taljacobson"><img src="https://avatars1.githubusercontent.com/u/13042769?v=4?s=100" width="100px;" alt=""/><br /><sub><b>Tal Jacobson</b></sub></a><br /><a href="#maintenance-taljacobson" title="Maintenance">🚧</a> <a href="https://github.com/aagarwal1012/IntroViews-Flutter/commits?author=taljacobson" title="Documentation">📖</a> <a href="#projectManagement-taljacobson" title="Project Management">📆</a></td>
    <td align="center"><a href="https://github.com/marloncepeda"><img src="https://avatars0.githubusercontent.com/u/25042632?v=4?s=100" width="100px;" alt=""/><br /><sub><b>marloncepeda</b></sub></a><br /><a href="https://github.com/aagarwal1012/IntroViews-Flutter/issues?q=author%3Amarloncepeda" title="Bug reports">🐛</a></td>
    <td align="center"><a href="https://medium.com/it-challenge"><img src="https://avatars0.githubusercontent.com/u/963316?v=4?s=100" width="100px;" alt=""/><br /><sub><b>Kravchenko Igor</b></sub></a><br /><a href="https://github.com/aagarwal1012/IntroViews-Flutter/issues?q=author%3AGorniv" title="Bug reports">🐛</a></td>
    <td align="center"><a href="https://github.com/SiDevesh"><img src="https://avatars2.githubusercontent.com/u/17254413?v=4?s=100" width="100px;" alt=""/><br /><sub><b>SiDevesh</b></sub></a><br /><a href="#ideas-SiDevesh" title="Ideas, Planning, & Feedback">🤔</a></td>
    <td align="center"><a href="https://have-you-been-here.com/"><img src="https://avatars2.githubusercontent.com/u/1579235?v=4?s=100" width="100px;" alt=""/><br /><sub><b>Slawa Pidgorny</b></sub></a><br /><a href="#ideas-spidgorny" title="Ideas, Planning, & Feedback">🤔</a></td>
    <td align="center"><a href="https://haideraltahan.com"><img src="https://avatars1.githubusercontent.com/u/4427929?v=4?s=100" width="100px;" alt=""/><br /><sub><b>Haider Al-Tahan</b></sub></a><br /><a href="#ideas-haideraltahan" title="Ideas, Planning, & Feedback">🤔</a></td>
    <td align="center"><a href="https://newerton.com"><img src="https://avatars3.githubusercontent.com/u/4175945?v=4?s=100" width="100px;" alt=""/><br /><sub><b>Newerton</b></sub></a><br /><a href="https://github.com/aagarwal1012/IntroViews-Flutter/issues?q=author%3Anewerton" title="Bug reports">🐛</a></td>
  </tr>
  <tr>
    <td align="center"><a href="https://www.discoos.org"><img src="https://avatars3.githubusercontent.com/u/866528?v=4?s=100" width="100px;" alt=""/><br /><sub><b>Kenneth Gulbrandsøy</b></sub></a><br /><a href="https://github.com/aagarwal1012/IntroViews-Flutter/issues?q=author%3Akengu" title="Bug reports">🐛</a> <a href="https://github.com/aagarwal1012/IntroViews-Flutter/commits?author=kengu" title="Tests">⚠️</a></td>
    <td align="center"><a href="https://www.linkedin.com/in/xsahil03x"><img src="https://avatars2.githubusercontent.com/u/25670178?v=4?s=100" width="100px;" alt=""/><br /><sub><b>Sahil Kumar</b></sub></a><br /><a href="https://github.com/aagarwal1012/IntroViews-Flutter/commits?author=xsahil03x" title="Tests">⚠️</a></td>
    <td align="center"><a href="https://www.yodsoft.com"><img src="https://avatars1.githubusercontent.com/u/2169309?v=4?s=100" width="100px;" alt=""/><br /><sub><b>Rodrigo Boratto</b></sub></a><br /><a href="https://github.com/aagarwal1012/IntroViews-Flutter/issues?q=author%3Arwrz" title="Bug reports">🐛</a></td>
    <td align="center"><a href="https://github.com/RKKgithub"><img src="https://avatars2.githubusercontent.com/u/63288678?v=4?s=100" width="100px;" alt=""/><br /><sub><b>RKKgithub</b></sub></a><br /><a href="https://github.com/aagarwal1012/IntroViews-Flutter/commits?author=RKKgithub" title="Code">💻</a></td>
    <td align="center"><a href="https://ir2pid.github.io"><img src="https://avatars.githubusercontent.com/u/907075?v=4?s=100" width="100px;" alt=""/><br /><sub><b>Sudipta Dutta</b></sub></a><br /><a href="https://github.com/aagarwal1012/IntroViews-Flutter/issues?q=author%3Air2pid" title="Bug reports">🐛</a></td>
    <td align="center"><a href="https://github.com/mzdm"><img src="https://avatars.githubusercontent.com/u/67197047?v=4?s=100" width="100px;" alt=""/><br /><sub><b>Matěj Žídek</b></sub></a><br /><a href="https://github.com/aagarwal1012/IntroViews-Flutter/issues?q=author%3Amzdm" title="Bug reports">🐛</a> <a href="https://github.com/aagarwal1012/IntroViews-Flutter/commits?author=mzdm" title="Code">💻</a> <a href="#platform-mzdm" title="Packaging/porting to new platform">📦</a> <a href="#maintenance-mzdm" title="Maintenance">🚧</a> <a href="#ideas-mzdm" title="Ideas, Planning, & Feedback">🤔</a> <a href="https://github.com/aagarwal1012/IntroViews-Flutter/commits?author=mzdm" title="Documentation">📖</a></td>
    <td align="center"><a href="https://github.com/ride4sun"><img src="https://avatars.githubusercontent.com/u/7740651?v=4?s=100" width="100px;" alt=""/><br /><sub><b>ride4sun</b></sub></a><br /><a href="https://github.com/aagarwal1012/IntroViews-Flutter/commits?author=ride4sun" title="Code">💻</a></td>
  </tr>
  <tr>
    <td align="center"><a href="https://github.com/zognotadog"><img src="https://avatars.githubusercontent.com/u/12435592?v=4?s=100" width="100px;" alt=""/><br /><sub><b>zognotadog</b></sub></a><br /><a href="https://github.com/aagarwal1012/IntroViews-Flutter/commits?author=zognotadog" title="Code">💻</a></td>
    <td align="center"><a href="https://github.com/Jayson1999"><img src="https://avatars.githubusercontent.com/u/44394801?v=4?s=100" width="100px;" alt=""/><br /><sub><b>Jayson</b></sub></a><br /><a href="https://github.com/aagarwal1012/IntroViews-Flutter/issues?q=author%3AJayson1999" title="Bug reports">🐛</a></td>
  </tr>
</table>

<!-- markdownlint-restore -->
<!-- prettier-ignore-end -->

<!-- ALL-CONTRIBUTORS-LIST:END -->

This project follows the [all-contributors](https://github.com/all-contributors/all-contributors) specification. Contributions of any kind welcome! See [Contributing.md](https://github.com/aagarwal1012/IntroViews-Flutter/blob/master/CONTRIBUTING.md).

# License

**IntroViews-Flutter** is licensed under `MIT license`.
