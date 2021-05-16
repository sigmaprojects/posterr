# Poster
Media display software for Plex, Sonarr and Radarr.

 > **Important Note** - Posterr now utilises data obtained via the _'Plex TV Series'_ agent. Whilst it will continue to work if you are _not_ using this agent, you will get mixed, to no results for TV theme tunes. It is _strongly_ recommended that you shift to this agent and scanner for your Plex libraries. (as recommended by Plex).

![Music playing](https://github.com/petersem/posterr/blob/master/doco/music.png?raw=true)
![Now screening](https://github.com/petersem/posterr/blob/master/doco/ns.png?raw=true)
![On-demand](https://github.com/petersem/posterr/blob/master/doco/od.png?raw=true)
![Coming soon](https://github.com/petersem/posterr/blob/master/doco/cs.png?raw=true)
![Landscape - background art mode](https://github.com/petersem/posterr/blob/master/doco/artmode.png?raw=true)
![Settings](https://github.com/petersem/posterr/blob/master/doco/settings.png?raw=true)

## Alpha software
This software is still considered `ALPHA` quality. (Still not feature complete) 
- **Check this page often for updates**

Visit the [wiki](https://github.com/petersem/posterr/wiki/Known-Issues) for more information on known issues.
 
## Features
 - Uses the latest 'Plex Agent' data (will work without tv themes for other agents).
 - Now Screening: Shows and movies from Plex.
 - Playing: Music from Plex.
 - On-demand: Random on-demand titles from multiple specified Plex libraries.
 - Coming Soon: Shows in Sonarr that are releasing in a given number of days (or Season premieres).
 - Coming Soon: Movies in Radarr that are releasing in a given number of days.
 - Option to play TV themes (available for most shows)
 - Option to play Movie themes if present, or a random MP3 of your choice for movies (add your own MP3 files)
 - Setup page (dark theme)
 - Built in Node JS, and packaged as a Docker image. (included image health check)
 - Now Screening / Playing displays a progress bar (green for direct play and red for transcoding)
 - Displays information for media, such as run time, content rating, studio, etc. 
 - Move the mouse cursor to the bottom footer of the page to hide it
 - Low resource usage. Memory: 20-35mb, Diskspace: 175mb, CPU: < 1% (running on a Synology NAS with a Celeron processor)
 - Checks for updates in Now Screening / Playing every 10 seconds (Will not display updates until browser refreshed or all slides cycled through)
 - Browser-based, so can run the app on one machine and a browser on another.
 - Background artwork option for slides (when available)

## Possible Uses
 - Mount a monitor on your wall (extra points if framed) and showcase your home media setup
 - Use it on a second monitor to keep an eye on what is running
 - Run it on a small screen mounted outside your theater room to show when a movie is in progress
 - Use a reverse proxy, or port-forward, to let your friends see what is playing, available, and coming soon

## Installation
Installation options are as follows:

### Docker Compose
Create the following directories in your docker folder:
 - .../docker/poster/config
 - .../docker/poster/randomthemes

```ya
version: '2.4'

services:
  posterr:
    image: petersem/poster
    container_name: posterr
    environment:
      TZ: Australia/Brisbane
    volumes:
      - ./docker/poster/randomthemes:/usr/src/app/public/randomthemes
      - ./docker/poster/config:/usr/src/app/config
    ports:
      - 3000:3000
```
#### Details
|Option|Details|
|--|--|
|TZ|Your local timezone. Go to [wikipedia](https://en.wikipedia.org/wiki/List_of_tz_database_time_zones) and use the `TZ Database Name` value.|
|/docker/poster/config|This is required to save your Posterr settings|
|/docker/poster/randomthemes|This is optional. If you add this, then you can populate this directory with your own MP3 files, which will play for movie slides|
|Ports|Change first part to a different port if needed. e.g. 9876:3000|

## Updates
 - Use containrr/watchtower to auto-update Posterr.
 
## Setup
Get to the settings page in a number of ways:
 - On initial load, you will be prompted.
 - Change the URL to _'http://hostIP:3000/settings'_
 - Clicking on the top banner title of any slide)
 - If on the 'no content' page, then click this text

*The default password is:* **raidisnotabackup**

Buttons are:
 - `Reload Saved` - Discards any changes and reloads last saved settings
 - `Main Page` - Navigates to main Posterr page (unsaved changes lost)
 - `Save` - Saves and restarts the application

 > Please see the [Posterr Wiki](https://github.com/petersem/posterr/wiki/Posterr-Configuration) for more information.

## Troubleshooting
Should you encounter a problem, the solution may be listed [HERE](https://github.com/petersem/posterr/wiki/Troubleshooting).

## Support
There is no _'official'_ support for this product, however should you encounter issues, raise an issue on the github page.

*Support my efforts and continued development* - Click this link to Buy me a coffee: 

 > ![](https://github.com/petersem/posterr/blob/master/doco/coffsmall.gif?raw=true) [Support development](https://paypal.me/thanksmp)

Thanks,

Matt Petersen (April 2021)

## Technical Details
Posterr uses the following:
 - Node & Node Express
 - The awesome [Node-Plex-APi](https://github.com/phillipj/node-plex-api)
 - Jquery
 - Bootstrap
 - Popper.js
 - Font-Awesome
 - Plex (via PlexAPI)
 - Sonarr (via API)
 - Radarr (via API)
 - Posters and artwork from Plex, TVDB and TMDB.

## License

MIT

**Free Software, Hell Yeah!**
