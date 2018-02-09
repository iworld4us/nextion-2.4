# Nextion 2.4", 2.8", 3.2", 4.3" Firmwares
Firmwares for Nextion 2.4", 2.8", 3.2", 4.3" displays to use with [MK4duo](https://github.com/MKFirmware/MK4duo) (3D Printer Arduino firmware).

Video demo: [youtu.be/Kq1StPYwWfQ](https://youtu.be/Kq1StPYwWfQ).

## If 3D GFX Preview is not working
Change these lines in `/src/lcd/nextion/Nextion_lcd.cpp`:

```cpp
if (strstr(buffer, "4827")) { // Model 4.3" Normal or Enhanced
        SERIAL_MSG(" 4.3");
        #if ENABLED(NEXTION_GFX)
          gfx.set_position(1, 24, 250, 155);
        #endif
}
else if (strstr(buffer, "8048")) { // Model 7" Normal or Enhanced
        SERIAL_MSG(" 7");
        #if ENABLED(NEXTION_GFX)
          gfx.set_position(274, 213, 250, 155);
        #endif
}
```

to:

```cpp
if (strstr(buffer, "3224")) { // Model 2.4" or 2.8" Normal or Enhanced
	SERIAL_MSG(" 2.4");
	#if ENABLED(NEXTION_GFX)
	  gfx.set_position(1, 24, 250, 155);
	#endif
}
else if (strstr(buffer, "4024")) {  // Model 3.2" Normal or Enhanced
	SERIAL_MSG(" 3.2");
	#if ENABLED(NEXTION_GFX)
	  gfx.set_position(1, 24, 250, 155);
	#endif
}
else if (strstr(buffer, "4827")) {  // Model 4.3" Normal or Enhanced
	SERIAL_MSG(" 4.3");
	#if ENABLED(NEXTION_GFX)
	gfx.set_position(1, 24, 250, 155);
	#endif
}
else if (strstr(buffer, "8048")) {  // Model 7" Normal or Enhanced
	SERIAL_MSG(" 7");
	#if ENABLED(NEXTION_GFX)
	  gfx.set_position(274, 213, 250, 155);
	#endif
}
```
