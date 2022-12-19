# d2s-editor

[Example](http://d2s.dschu012.dev/)

This is a basic Diablo 2 save editor for D2 and D2R. The parser uses the TXT data from the Diablo 2 MPQs so the editor could be repurposed for basic TXT mods. Some of the main features are:

* Modify basic stats (str/lvl/gold/etc...)
* Modify quest status
* Modify waypoints
* Import items (~1000 different items to import)
* Modify basic stats on items
* Copy item between chars (drag between browser windows)

### How to use on your own mod

1. Clone this repo or download a zip.
2. Extract your MPQ data to a public/data folder in the same directory as the repo. (the tool needs TXTs, strings, pallettes, and item dc6s to work properly)
3. Run 
```
npm install 
npm run serve
```
4. Go to http://localhost:${PORT}/ verify everything works.
