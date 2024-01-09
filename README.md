**To use framework - simply include it to your script and start to work.**

If you will get error "Authorization required, but no authorization protocol specified" on your desktop - you should install tool "xhost" and run following command from current user in terminal: 
```
xhost + local:
```

Following is simple example which will draw white filled rectangle on your screen with 50% of width and 50% of height:
```php
<?php
require 'Xlib.php';
$display = XDisplay::create();
$bg = $display->allocColor($display->screens[0]->colormap, 0xffff, 0xffff, 0xffff);
$wnd = $display->createWindow($display->screens[0]->rootWindow,0, 0,
$display->screens[0]->width/2, $display->screens[0]->height/2, 0,
XClient::InputOutput, null, array('backgroundPixel' => $bg['pixel'],
'eventMask'=>XClient::ExposureMask | XClient::KeyPressMask | XClient::StructureNotifyMask,
'overrideRedirect'=>true));
$display->mapWindow($wnd);
for (;;) {
}
```
