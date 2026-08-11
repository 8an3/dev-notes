# UTILS

> [!NOTE]
>
> My apologies, this file seems to be one of the few that didn't make the latest docs conversion.

## <img src="https://raw.githubusercontent.com/8an3/midgardr-notes/main/utils/vulknut.png" width="32"  style="vertical-align: middle; margin-bottom: 4px;"> SVG To WOFF

Just as its named its a svg to woff converter, converts your entire folder into and places the produced woff file within the same folder.

Be sure to remove all non svg files as it will error out if the folder contains anything but svgs.

Can be executed via the devstack menu, option labeled 'SVG to WOFF'



## <img src="https://raw.githubusercontent.com/8an3/midgardr-notes/main/utils/vulknut.png" width="32"  style="vertical-align: middle; margin-bottom: 4px;"> env Context Swapper

I've implemented multiple systems in the past, this seems to work the quickest and cleanest, as you only click once and it swaps everything for you.

I find whenever working with more than one .env variable I'm already placing 2 values in my .env anyways, but having to go manually cutting and pasting to swap out values. Obviously this being a lot quicker at it.

2 files are needed for this
- .env
- .dev.env

In order for it to tell what to swap where when it is triggered you must place the following values at the start of the .env key
- 'LOCAL_'
- 'REMOTE_'

Currently only usable via the devstack menu as I haven't found a way to trigger it via a config item in the devstack explorer pane. I might try again in the future but in its current form it works great.

Whenever you select remote or local, scans the .dev.env file for the relative desired values for example selecting local will swap out all the values that have a local entry in the .env file no matter how many you have to swap out.