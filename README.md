To use framework - simply include it to your script and start to work.

If you will get error "Authorization required, but no authorization protocol specified" on your desktop - you should install tool "xhost" and run following command from current user in terminal: xhost + local:
```
<?php
require 'Xlib.php';
$x = XDisplay::create();
$bc = $x->allocColor($x->screens[0]->colormap, 0xffff, 0xffff, 0xffff);
$wnd = $x->createWindow($x->screens[0]->rootWindow,0, 0, $x->screens[0]->width/2, $x->screens[0]->height/2, 0, XClient::InputOutput, null,array('backgroundPixel' => $bc['pixel'],'eventMask' => XClient::ExposureMask | XClient::KeyPressMask | XClient::StructureNotifyMask, 'overrideRedirect' => true));
$x->mapWindow($wnd);
for (;;) {
}
```
