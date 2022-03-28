# 🖥 Bento-next
## A fork of Bento, the simple, customizable, and beautiful startpage written with Vue.js 3 and TailwindCSS! 
## [Demo](https://dash.lew.ooo)
![image](assets/header.png)
<br />
[Upstream](https://github.com/migueravila/Bento)

<a name="index"></a>
## 👇 Index
- [👇 Index](#index)
- [✨ Features](#features)
- [🚀 Usage](#usage)
  - [🐬 In a Docker Container](#docker)
  - [💾 With a web server](#httpserve)
- [🎨 Customization](#customization)
  - [🛠️ General](#general)
  - [🕓 Clock](#clock)
  - [🎨 Themes](#themes)
  - [🔍 Search Bar](#search)
  - [👋 Greetings](#greetings)
  - [📐 Layouts](#layouts)
  - [⛈️ Weather](#️weather)
  - [🏷️ Buttons & Lists](#️buttons)
  - [🌑 Auto change theme](#autochange)
- [🍴 Changes and Contributing](#contribute)
  - [🖌️ Custom Themes](#customthemes)
  - [📂 Contributing Changes](#changes)

<a name="features"></a>
## ✨ Features
- **Themes** Bento-next ships with 9 included themes, such as Nord, Arc, and Solarized, each with their own light/dark palletes.
- **Local storage** Using someone else's instance? Change the theme and name for you and you only with the theme menu, or by clicking the name text.
- **Easy configuration** with the included `config.js` file.
- **Dark/Light**, toggleable through your browser.
- **Layouts!** adjust the layout of Bento to fit your needs and workflow.
- **Clock and Date** 24/12 hour, with an optional animated separator.
- **Greetings** are easy to modify.
- **Icons** Bento-next supports a huge array of icons from [FontAwesome](https://fontawesome.com).

<a name="usage"></a>
## 🚀 Usage

Currently, Bento-next needs to be hosted, although this will change soon!
<a name="docker"></a>
### 🐬 In a Docker Container

You can run Bento in a Docker Container, either with `docker run`, or with the included `docker-compose` file.

#### Docker run
 1. Clone this repo to pull the config.js file: `git clone https://github.com/lewisdoesstuff/bento-next/`
 2. Run the following `docker` command, providing the path to the config.js file, changing port mappings if needed.
 3. `# docker run -it -d -p 80:8080 -v <config.js location>:/usr/share/nginx/html/config.js lewisdoesstuff/bento-next`

#### docker-compose
  1. Clone this repo with `git clone https://github.com/lewisdoesstuff/bento-next/`
  2. Edit port mappings, and provide a path to the config.js file in `docker-compose.yml`
  3. `cd` into the cloned repo, then run `# docker-compose -d up` to start. 

<a name="httpserve"></a>
### 💾 With a web server (nginx, apache, etc...)

  #### Building Bento
  1. Clone this repo with `git clone https://github.com/lewisdoesstuff/bento-next/`
  2. `cd bento-next` to enter the cloned repo.
  3. `npm install` to install node modules.
  4. `npm run build` to build the app.
  5. Copy the files placed in `./dist` to your webservers html directory. eg: `cp ./dist/* /usr/share/nginx/html -r` 

<a name="customization"></a>
## 🔧 Customization

All settings can be managed in the `config.js` file:
<a name="general"></a>
### 🛠️ General

Change the default name (displayed to all users), choose if links open in a new tab, and change the window title.

```js
  // General
  name: "John",
  openInNewTab: true,
  title: "Bento",
```
<a name="clock"></a>
### 🕓 Clock

Adjust 12/24hr format, or enable an animated separator.

```js
  // Clock
  twelveHourFormat: false,
  flashSeparator: false,
```
<a name="themes"></a>
### 🎨 Themes

Bento-next supports 9 pre-included themes, if you'd like to add more, please see the steps at [Custom Themes](#customthemes)
Included themes: 
  
  - [Arc](https://github.com/horst3180/arc-theme)
  - Bento (default)
  - [Catppuccin](https://github.com/catppuccin/catppuccin)
  - [Concept-Dark](https://www.deviantart.com/zb652/art/Concept-Dark-885878180)
  - [Monokai (free)](https://monokai.pro/)
  - [Nord](https://www.nordtheme.com/)
  - Sakura
  - [Solarized](https://ethanschoonover.com/solarized/)
  - [Summer](https://github.com/JhonnyRice/summer)

```js
// Theme
  theme: "bento",
  imageBackground: false,
  imageUrl: "./assets/background.jpg",
  themes: [   // List of installed themes, add your own themes in ./src/assets/css/themes and include it in the array below.
    "arc",
    "bento",
    "catppuccin",
    "conceptdark", // dark mode only
    "monokai",
    "nord",
    "sakura",
    "solarized",
    "summer"
  ],
```
<a name="search"></a>
### 🔍 Search Bar

Bento-next includes a search bar by default, with 4 themes to choose from. If you'd like to add your own, you'll have to do this in the app's source (for now). You can find the search bar at `./src/components/SearchBar.vue`.
```js
  // Search Bar
  searchBar: true,
  searchEngine: "google", // google, ddg
  barStyle: "bento", // bento, minimal, boxy, rounded
  barPlaceholder: "", // if blank, use search engine name. Set to ' ' for no placeholder.
  autoFocusBar: true,
```
<a name="greetings"></a>
### 👋 Greetings

Edit the displayed greetings for morning, afternoon, evening, and night.
```js
  // Greetings
  greetingMorning: "Good morning,",
  greetingAfternoon: "Good afternoon,",
  greetingEvening: "Good evening,",
  greetingNight: "Sweet dreams,",
  ```
<a name="layouts"></a>
### 📐 Layouts

Bento has three different layouts `bento`, `lists`, and `buttons`. `Bento` is a split with buttons on the left and lists on the right. `Lists` swaps the buttons out for another list container, and `buttons` does the same with buttons. 
```js
  // Layout
  bentoLayout: 'bento', // 'bento', 'lists', 'buttons'
```

If you want to customize all your extra buttons and lists go to [🏷️ Buttons & Lists](#️buttons).

<a name="weather"></a>
### ⛈️ Weather

Bento provides a weather widget that pulls data from OpenWeatherMap. To use this, you'll need to add an API key to the settings. You can generate a free API key from [OpenWeatherMap](https://openweathermap.org/api). You'll need a "Current Weather Data" key.  
You can provide a default lat/long, or have Bento automatically pull your location from your browsers location data. 
If this isn't available, or you deny location permissions, Bento will fall back to using the lat/long set in the config.

Finally, choose an icon set:

- **OneDark** (_Default_) Using the One Dark Pro color scheme
- **Nord** Using the Nord Color Scheme
- **Dark** For White theme only users that want a minimalist look
- **White** For Dark theme only users that want a minimalist look

```js
  // Weather
  weatherKey: "YourOpenWeatherMapAPIKey", // Write here your API Key
  weatherIcons: "OneDark", // 'Onedark', 'Nord', 'Dark', 'White'
  weatherUnit: "C", // 'F', 'C'
  language: "en", // More languages in https://openweathermap.org/current#multi

  trackLocation: true, // Request location from the browser. If false, or location is denied, use the coordinates below.
  defaultLatitude: "37.775",
  defaultLongitude: "-122.419",
```

<a name="buttons"></a>
### 🏷️ Buttons & Lists

Every entry in the buttons or lists containers are editable through here! A breakdown of the object is below.
```js
  itemContainer: [
    {
      id: "1", // entry ID, don't modify.
      name: "Github", // set the name of the card
      icon: "fab-github", // provide a FontAwesome icon name. Regular icons (fa-) don't require a prefix, while FA-Brands icons must be prefixed with "fab-"
      link: "https://github.com", // provide a link to the page.
    },
    {
      id: "2",
      name: "GMail",
      icon: "envelope",
      link: "https://mail.google.com/",
    },
  ]
```

<a name="autochange"></a>
### 🌑 Auto change theme

**Note: The below options don't currently work in bento-next. Coming very soon!**

The theme can be automatically changed by the OS' current theme or personalized hours
that you can change in the `config.js` file:

```js
  // Autochange theme from OS preferece
  changeThemeByOS: true,

  // Switch theme based on set hours. (24hr format, string must be in: hh:mm)
  changeThemeByHour: false,
  hourDarkThemeActive: "18:30",
  hourDarkThemeInactive: "07:00",

  // Switch dark theme automatically from sunrise to sunset. Pulls from the browsers location, or falls back to the defaults if not.
  // Requires an OpenWeatherMap API key.
  changeThemeByLocation: false,
```



<a name="contribute">

# 🍴 Changes and Contributing

<a name="customthemes"></a>

## 🖌️ Custom Themes

Bento can be expanded with user-defined themes! To create one, add a new .css file to `./public/css/themes/`, then add it to the array of themes in `config.js`.
If you've got a theme you'd like to see included, please open a PR, or open an issue with a link to the color palette.
Example:

```css
:root {
  /* Light Colors  */

  --background: #f5f5f5; /* Background color */
  --accent: #57a0d9; /* Hover color */
  --cards: #e4e6e6; /* Cards color */

  /* Fonts Color */
  --fg: #3a3a3a; /* Foreground color */
  --sfg: #494949; /* Sceondary Foreground color */

  /* Image background  */
  --imgcol: linear-gradient(rgba(255, 255, 255, 0.7), rgba(255, 255, 255, 0.7)); /* Filter color */

  /* Dark Colors  */

  --darkbackground: #19171a; /* Background color */
  --darkaccent: #57a0d9; /* Hover color */
  --darkcards: #201e21; /* Cards color */

  /* Fonts Color */
  --darkfg: #d8dee9; /* Foreground color */
  --darksfg: #2c292e; /* Secondary Foreground color */

  /* Image background  */
  --darkimgcol: linear-gradient(rgba(0, 0, 0, 0.85), rgba(0, 0, 0, 0.85)); /* Filter color */
}
```
<a name="changes">

## 📂 Contributing Changes

I'd be thrilled to hear about any changes that you've made to the project!  
If you feel that these would work as a default feature, please submit a PR with your changes!  
For anything that you feel may be better suited to the upstream project, please port your changes to vanilla HTML/JS and open a PR on [migueravila/Bento](https://github.com/migueravila/Bento).

While I don't have a specific contributing guide, or code style to follow, please ensure your changes follow the general style of the program, and respect any existing features (no breaking changes, please!)  
Please ensure that any PR's don't contain changes to the default `config.js` values, unless you need to add another. Please also ensure to remove your OpenWeatherMap API key!

