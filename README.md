# Performance enhanced version

Changes have been made to the Adafruit.cpp drawChar() funtion to improve rendering speed of the free fonts significantly.

To aid performance enhancment tests there are #define switches within that function as follows:

If FAST_LINE is #defined then the free fonts are rendered using horizontal lines this makes rendering fonts 2-5 times faster. Particularly good for large fonts.
This is an elegant solution since it still uses generic functions present in the stock library.

If FAST_SHIFT is defined then a slightly faster (for AVR) shifting bit mask is used. The performance gain is small but worthwhile at 10%.

The overal performance gain will be dependant on the font and how many multipixel horizontal lines are in the rendered character. Even small fonts show a significant perfromance improvement even thout there are many single pixel plots needed.

The test case for the performance test here is to print "Hello world" (lower case w) in different fonts. 

# Adafruit GFX Library

This is the core graphics library for all our displays, providing a common set of graphics primitives (points, lines, circles, etc.). It needs to be paired with a hardware-specific library for each display device we carry (to handle the lower-level functions).

Adafruit invests time and resources providing this open source code, please support Adafruit and open-source hardware by purchasing products from Adafruit!

Written by Limor Fried/Ladyada for Adafruit Industries.
BSD license, check license.txt for more information.
All text above must be included in any redistribution.

Recent Arduino IDE releases include the Library Manager for easy installation. Otherwise, to download, click the DOWNLOAD ZIP button, uncompress and rename the uncompressed folder Adafruit_GFX. Confirm that the Adafruit_GFX folder contains Adafruit_GFX.cpp and Adafruit_GFX.h. Place the Adafruit_GFX library folder your <arduinosketchfolder>/Libraries/ folder. You may need to create the Libraries subfolder if its your first library. Restart the IDE.

# Useful Resources

- Image2Code: This is a handy Java GUI utility to convert a BMP file into the array code necessary to display the image with the drawBitmap function. Check out the code at ehubin's GitHub repository: https://github.com/ehubin/Adafruit-GFX-Library/tree/master/Img2Code

- drawXBitmap function: You can use the GIMP photo editor to save a .xbm file and use the array saved in the file to draw a bitmap with the drawXBitmap function. See the pull request here for more details: https://github.com/adafruit/Adafruit-GFX-Library/pull/31

- 'Fonts' folder contains bitmap fonts for use with recent (1.1 and later) Adafruit_GFX. To use a font in your Arduino sketch, #include the corresponding .h file and pass address of GFXfont struct to setFont(). Pass NULL to revert to 'classic' fixed-space bitmap font.

- 'fontconvert' folder contains a command-line tool for converting TTF fonts to Adafruit_GFX .h format.
