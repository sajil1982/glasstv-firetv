# firetv-photo

The Fire TV setup from glasstv's own testing: one row of monochrome app tiles, a 12-hour clock with the date,
and a **photo wallpaper that follows the time of day** (dawn, day, dusk, night, switched at your local sunrise
and sunset).

No photo ships with this theme — use your own (a wide sunset or golden-hour shot works best: the script treats
it as the dusk picture and grades the other three from it):

```sh
pip install numpy pillow
python3 tools/wallpaper-generators/photo_timeofday.py my-photo.jpg themes/firetv-photo/wallpapers
```

That writes `dawn-clear.jpg`, `day-clear.jpg`, `dusk-clear.jpg` and `night-clear.jpg`. Then set your
location in `launcher/app/src/main/res/values/config.xml` (`latitude` / `longitude`, used for sunrise and
sunset) and push the theme:

```sh
tools/theme.sh themes/firetv-photo          # or tools\theme.ps1 themes\firetv-photo on Windows
```

`weather_wallpaper` is on by default; with only the `-clear` pictures the launcher uses them in every weather.

## Fire TV extras in this theme

- `stock_home_redirect` makes the Home button open glasstv (see the main README for the one-time ADB setup).
- A **Live TV** button in the top bar opens Amazon's live TV guide (`top_bar_apps` + `launch_actions`).
- Hik-Connect (`com.connect.enduser`) sits in the app library and gets landscape + the remote pointer; swap in your own touch-only apps.
