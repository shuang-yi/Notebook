# gmt.conf文件

## COLOR Parameters
```
#
COLOR_BACKGROUND		= black
COLOR_FOREGROUND		= white
COLOR_NAN			= 127.5
COLOR_MODEL			= none
COLOR_HSV_MIN_S			= 1
COLOR_HSV_MAX_S			= 0.1
COLOR_HSV_MIN_V			= 0.3
COLOR_HSV_MAX_V			= 1
#

```
## DIR Parameters
```
#
DIR_DATA			= 
DIR_DCW				= 
DIR_GSHHG			= /Users/Yish/my-program/GMT-5.1.1.app/Contents/Resources/share/coast
DIR_TMP				= 
DIR_USER			= 
#
```
## FONT Parameters
```
#
FONT_ANNOT_PRIMARY		= 10p,Helvetica,black
FONT_ANNOT_SECONDARY		= 14p,Helvetica,black
FONT_LABEL			= 16p,Helvetica,black
FONT_LOGO			= 8p,Helvetica,black
FONT_TITLE			= 24p,Helvetica,black
#
```
## FORMAT Parameters
```
#
FORMAT_CLOCK_IN			= hh:mm:ss
FORMAT_CLOCK_OUT		= hh:mm:ss
FORMAT_CLOCK_MAP		= hh:mm:ss
FORMAT_DATE_IN			= yyyy-mm-dd
FORMAT_DATE_OUT			= yyyy-mm-dd
FORMAT_DATE_MAP			= yyyy-mm-dd
FORMAT_GEO_OUT			= D
FORMAT_GEO_MAP			= ddd:mm:ss
FORMAT_FLOAT_OUT		= %.12g
FORMAT_FLOAT_MAP		= %.12g
FORMAT_TIME_PRIMARY_MAP		= full
FORMAT_TIME_SECONDARY_MAP	= full
FORMAT_TIME_STAMP		= %Y %b %d %H:%M:%S
#

```
## GMT Miscellaneous Parameters
```
#
GMT_COMPATIBILITY		= 4
GMT_CUSTOM_LIBS			= 
GMT_EXTRAPOLATE_VAL		= NaN
GMT_FFT				= auto
GMT_HISTORY			= true
GMT_INTERPOLANT			= akima
GMT_TRIANGULATE			= Shewchuk
GMT_VERBOSE			= compat
#

```
## I/O Parameters
```
#
IO_COL_SEPARATOR		= tab
IO_GRIDFILE_FORMAT		= nf
IO_GRIDFILE_SHORTHAND		= false
IO_HEADER			= false
IO_N_HEADER_RECS		= 0
IO_NAN_RECORDS			= pass
IO_NC4_CHUNK_SIZE		= auto
IO_NC4_DEFLATION_LEVEL		= 3
IO_LONLAT_TOGGLE		= false
IO_SEGMENT_MARKER		= >
#

```
## MAP Parameters
```
#
MAP_ANNOT_MIN_ANGLE		= 20
MAP_ANNOT_MIN_SPACING		= 0p
MAP_ANNOT_OBLIQUE		= 1
MAP_ANNOT_OFFSET_PRIMARY	= 3p
MAP_ANNOT_OFFSET_SECONDARY	= 3p
MAP_ANNOT_ORTHO			= we
MAP_DEFAULT_PEN			= default,black
MAP_DEGREE_SYMBOL		= ring
MAP_FRAME_AXES			= WESNZ
MAP_FRAME_PEN			= thicker,black
MAP_FRAME_TYPE			= plain
MAP_FRAME_WIDTH			= 5p
MAP_GRID_CROSS_SIZE_PRIMARY	= 0p
MAP_GRID_CROSS_SIZE_SECONDARY	= 0p
MAP_GRID_PEN_PRIMARY		= default,black
MAP_GRID_PEN_SECONDARY		= thinner,black
MAP_LABEL_OFFSET		= 8p
MAP_LINE_STEP			= 0.75p
MAP_LOGO			= false
MAP_LOGO_POS			= BL/-54p/-54p
MAP_ORIGIN_X			= 1i
MAP_ORIGIN_Y			= 1i
MAP_POLAR_CAP			= 85/90
MAP_SCALE_HEIGHT		= 5p
MAP_TICK_LENGTH_PRIMARY		= 3p/1.5p
MAP_TICK_LENGTH_SECONDARY	= 9p/2.25p
MAP_TICK_PEN_PRIMARY		= thinner,black
MAP_TICK_PEN_SECONDARY		= thinner,black
MAP_TITLE_OFFSET		= 14p
MAP_VECTOR_SHAPE		= 0
#

```
## Projection Parameters
```
#
PROJ_AUX_LATITUDE		= authalic
PROJ_ELLIPSOID			= WGS-84
PROJ_LENGTH_UNIT		= cm
PROJ_MEAN_RADIUS		= authalic
PROJ_SCALE_FACTOR		= default
#

```
## PostScript Parameters
```
#
PS_CHAR_ENCODING		= ISOLatin1+
PS_COLOR_MODEL			= rgb
PS_COMMENTS			= false
PS_IMAGE_COMPRESS		= lzw
PS_LINE_CAP			= butt
PS_LINE_JOIN			= miter
PS_MITER_LIMIT			= 35
PS_MEDIA			= a4
PS_PAGE_COLOR			= white
PS_PAGE_ORIENTATION		= landscape
PS_SCALE_X			= 1
PS_SCALE_Y			= 1
PS_TRANSPARENCY			= Normal
#

```
## Calendar/Time Parameters
```
#
TIME_EPOCH			= 1970-01-01T00:00:00
TIME_IS_INTERVAL		= off
TIME_INTERVAL_FRACTION		= 0.5
TIME_LANGUAGE			= us
TIME_UNIT			= s
TIME_WEEK_START			= Monday
TIME_Y2K_OFFSET_YEAR		= 1950

```

# GMT5 图示
![c500](media/14830011268462/14830017196828.jpg)
![c500](media/14830011268462/14830017292279.jpg)
![c500](media/14830011268462/14830017371241.jpg)

# GMT4配置文件

```
#
#	GMT-SYSTEM 4.5.12 [64-bit] Defaults file
#
#-------- Plot Media Parameters -------------
PAGE_COLOR		= white
PAGE_ORIENTATION	= landscape
PAPER_MEDIA		= a4
#-------- Basemap Annotation Parameters ------
ANNOT_MIN_ANGLE		= 20
ANNOT_MIN_SPACING	= 0
ANNOT_FONT_PRIMARY	= Helvetica
ANNOT_FONT_SIZE_PRIMARY	= 10p
ANNOT_OFFSET_PRIMARY	= 0.105833c
ANNOT_FONT_SECONDARY	= Helvetica
ANNOT_FONT_SIZE_SECONDARY	= 16p
ANNOT_OFFSET_SECONDARY	= 0.2c
DEGREE_SYMBOL		= ring
HEADER_FONT		= Helvetica
HEADER_FONT_SIZE	= 20p
HEADER_OFFSET		= 0.5c
LABEL_FONT		= Helvetica
LABEL_FONT_SIZE		= 16p
LABEL_OFFSET		= 0.3c
OBLIQUE_ANNOTATION	= 1
PLOT_CLOCK_FORMAT	= hh:mm:ss
PLOT_DATE_FORMAT	= yyyy-mm-dd
PLOT_DEGREE_FORMAT	= ddd:mm:ss
Y_AXIS_TYPE		= hor_text
#-------- Basemap Layout Parameters ---------
BASEMAP_AXES		= WESN
BASEMAP_FRAME_RGB	= black
BASEMAP_TYPE		= plain
FRAME_PEN		= 1.25p
FRAME_WIDTH		= 0.2c
GRID_CROSS_SIZE_PRIMARY	= 0c
GRID_PEN_PRIMARY	= 0.25p
GRID_CROSS_SIZE_SECONDARY	= 0c
GRID_PEN_SECONDARY	= 0.5p
MAP_SCALE_HEIGHT	= 0.2c
POLAR_CAP		= 85/90
TICK_LENGTH		= 0.105833c
TICK_PEN		= 0.5p
X_AXIS_LENGTH		= 25c
Y_AXIS_LENGTH		= 15c
X_ORIGIN		= 2.5c
Y_ORIGIN		= 2.5c
UNIX_TIME		= FALSE
UNIX_TIME_POS		= BL/-2c/-2c
UNIX_TIME_FORMAT	= %Y %b %d %H:%M:%S
#-------- Color System Parameters -----------
COLOR_BACKGROUND	= black
COLOR_FOREGROUND	= white
COLOR_NAN		= 128
COLOR_IMAGE		= adobe
COLOR_MODEL		= rgb
HSV_MIN_SATURATION	= 1
HSV_MAX_SATURATION	= 0.1
HSV_MIN_VALUE		= 0.3
HSV_MAX_VALUE		= 1
#-------- PostScript Parameters -------------
CHAR_ENCODING		= ISOLatin1+
DOTS_PR_INCH		= 300
GLOBAL_X_SCALE		= 1
GLOBAL_Y_SCALE		= 1
N_COPIES		= 1
PS_COLOR		= rgb
PS_IMAGE_COMPRESS	= lzw
PS_IMAGE_FORMAT		= ascii
PS_LINE_CAP		= butt
PS_LINE_JOIN		= miter
PS_MITER_LIMIT		= 35
PS_VERBOSE		= FALSE
TRANSPARENCY		= 0
#-------- I/O Format Parameters -------------
D_FORMAT		= %.12lg
FIELD_DELIMITER		= tab
GRIDFILE_FORMAT		= nf
GRIDFILE_SHORTHAND	= FALSE
INPUT_CLOCK_FORMAT	= hh:mm:ss
INPUT_DATE_FORMAT	= yyyy-mm-dd
IO_HEADER		= FALSE
N_HEADER_RECS		= 1
NAN_RECORDS		= pass
OUTPUT_CLOCK_FORMAT	= hh:mm:ss
OUTPUT_DATE_FORMAT	= yyyy-mm-dd
OUTPUT_DEGREE_FORMAT	= D
XY_TOGGLE		= FALSE
#-------- Projection Parameters -------------
ELLIPSOID		= WGS-84
MAP_SCALE_FACTOR	= default
MEASURE_UNIT		= cm
#-------- Calendar/Time Parameters ----------
TIME_FORMAT_PRIMARY	= full
TIME_FORMAT_SECONDARY	= full
TIME_EPOCH		= 2000-01-01T12:00:00
TIME_IS_INTERVAL	= OFF
TIME_INTERVAL_FRACTION	= 0.5
TIME_LANGUAGE		= us
TIME_UNIT		= d
TIME_WEEK_START		= Sunday
Y2K_OFFSET_YEAR		= 1950
#-------- Miscellaneous Parameters ----------
HISTORY			= TRUE
INTERPOLANT		= akima
LINE_STEP		= 0.025c
VECTOR_SHAPE		= 0
VERBOSE			= FALSE

```
