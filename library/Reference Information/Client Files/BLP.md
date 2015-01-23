[![](/wiki/icons/home.gif)](/wiki/Home.md)

----------

## Introduction

BLP files are used as texture storage. The textures can be stored with a 256 color palette or full 24bit RGB colors. The format supports 1, 4 and 8-bit alpha transparency and DXT compression. 
The file format is NOT chunked.
Wikipedia has a nice overview over the format: <http://en.wikipedia.org/wiki/.BLP>

## Header

From <http://www.pxr.dk/wowdev/wiki/index.php?title=BLP>

    Offset   Type            Description
    -------------------------------------------------------------------------------------------------------
    0x00     char[4]         always 'BLP2'
    0x04     uint32          Type, always 1
    0x08     uint8           Compression: 1 for uncompressed, 2 for DXTC
    0x09     uint8           Alpha channel bit depth: 0, 1 or 8
    0x0A     uint8           Alpha encoding 
    0x0B     uint8           Has MipMaps? 
    0x0C     uint32          X resolution (power of 2)
    0x10     uint32          Y resolution (power of 2)
    0x14     uint32[16]      offsets for every mipmap level (or 0 when there is no more mipmap level)
    0x54     uint32[16]      sizes for every mipmap level (or 0 when there is no more mipmap level)
    0x94     uint32[256]     palette of 256 BGRA Values

If HasMipMaps is 0, there is only 1 mipmap level.
The palette is always present, even if it is not used. In that case all values are 0.

## Encoding Schemes

**Type 1 Compression 1 AlphaDepth 0 (uncompressed paletted image with no alpha)**

Each byte of the image data is an index into Palette which contains the actual RGB value for the pixel. Although the palette entries are 32-bits, the alpha value of each Palette entry may contain garbage and should be discarded.

**Type 1 Compression 1 AlphaDepth 1 (uncompressed paletted image with 1-bit alpha)**

This is the same as Type 1 Encoding 1 AlphaDepth 0 except that immediately following the index array is a second image array containing 1-bit alpha values for each pixel. The first byte of the array is for pixels 0 through 7, the second byte for pixels 8 through 15 and so on. Bit 0 of each byte corresponds to the first pixel (leftmost) in the group, bit 7 to the rightmost. A set bit indicates the pixel is opaque while a zero bit indicates a transparent pixel.

**Type 1 Compression 1 AlphaDepth 8 (uncompressed paletted image with 8-bit alpha)**

This is the same as Type 1 Encoding 1 AlphaDepth 0 except that immediately following the index array is a second image array containing the actual 8-bit alpha values for each pixel. This second array starts at **BLP2Header.Offset[0] + BLP2Header.Width * BLP2Header.Height**.

***
**Type 1 Compression 2 AlphaDepth 0 (DXT1 no alpha)**

The image data are formatted using DXT1 compression with no alpha channel.

**Type 1 Compression 2 AlphaDepth 1 (DXT1 one bit alpha)**

The image data are formatted using DXT1 compression with a one-bit alpha channel.

**Type 1 Compression 2 AlphaDepth 4 AlphaEncoding 1 (DXT3 four bits alpha)**

The image data are formatted using DXT3 compression.

**Type 1 Compression 2 AlphaDepth 8 AlphaEncoding 1 (DXT3 eight bits alpha)**

The image data are formatted using DXT3 compression.

**Type 1 Compression 2 AlphaDepth 8 AlphaEncoding 7 (DXT5)**

The image data are formatted using DXT5 compression.


## DXT Compression

BLP only uses DXT 1,3 and 5.
From: <http://en.wikipedia.org/wiki/DXTn>

### DXT1
DXT1 (also known as Block Compression 1 or BC1) is the smallest variation of S3TC, storing 16 input pixels in 64 bits of output, consisting of two 16-bit RGB 5:6:5 color values and a 4x4 two bit lookup table.

If the first color value (c<sub>0</sub>) is numerically greater than the second color value (c<sub>1</sub>), then two other colors are calculated, such that 

<pre>c<sub>2</sub> = 2/3 c<sub>0</sub> + 1/3 c<sub>1</sub></pre>
and 
<pre>c<sub>3</sub> = 1/3 c<sub>0</sub> + 2/3 c<sub>1</sub></pre>

Otherwise, if c<sub>0</sub> <= c<sub>1</sub>, then 
<pre> c<sub>2</sub> = 1/2 c<sub>0</sub> + 1/2 c<sub>1</sub></pre>
and c<sub>3</sub> is transparent black corresponding to a premultiplied alpha format.

The lookup table is then consulted to determine the color value for each pixel, with a value of 0 corresponding to  c<sub>0</sub>  and a value of 3 corresponding to c<sub>3</sub> . DXT1 does not store alpha data enabling higher compression ratios.

### DXT3 
DXT3 (also known as Block Compression 2 or BC2) converts 16 input pixels (corresponding to a 4x4 pixel block) into 128 bits of output, consisting of 64 bits of alpha channel data (4 bits for each pixel) followed by 64 bits of color data, encoded the same way as DXT1 (with the exception that the 4 color version of the DXT1 algorithm is always used instead of deciding which version to use based on the relative values of c<sub>0</sub> and c<sub>1</sub> ).

In DXT3, the color data is interpreted as not having been premultiplied by alpha. Typically DXT2/3 are well suited to images with sharp alpha transitions, between translucent and opaque areas.

### DXT5 
DXT5 (also known as Block Compression 3 or BC3) converts 16 input pixels into 128 bits of output, consisting of 64 bits of alpha channel data (two 8 bit alpha values and a 4x4 3 bit lookup table) followed by 64 bits of color data (encoded the same way as DXT2 and DXT3).

If α<sub>0</sub> > α<sub>1</sub>, then six other alpha values are calculated, such that <pre>α<sub>2</sub> = (6α<sub>0</sub> + 1α<sub>1</sub>) / 7, 
α<sub>3</sub> = (5α<sub>0</sub> + 2α<sub>1</sub>) / 7,
α<sub>4</sub> = (4α<sub>0</sub> + 3α<sub>1</sub>) / 7, 
α<sub>5</sub> = (3α<sub>0</sub> + 4α<sub>1</sub>) / 7, 
α<sub>6</sub> = (2α<sub>0</sub> + 5α<sub>1</sub>) / 7, 
α<sub>7</sub> = (1α<sub>0</sub> + 6α<sub>1</sub>) / 7</pre>

Otherwise, if α<sub>0</sub> <= α<sub>1</sub>, four other alpha values are calculated such that 
<pre>α<sub>2</sub> = (4α<sub>0</sub> + 1α<sub>1</sub>) / 5, 
α<sub>3</sub> = (3α<sub>0</sub> + 2α<sub>1</sub>) / 5, 
α<sub>4</sub> = (2α<sub>0</sub> + 3α<sub>1</sub>) / 5, 
α<sub>5</sub> = (1α<sub>0</sub> + 4α<sub>1</sub>) / 5,
α<sub>6</sub> = 0,
α<sub>7</sub> = 255</pre>

The lookup table is then consulted to determine the alpha value for each pixel, with a value of 0 corresponding to α<sub>0</sub> and a value of 7 corresponding to α<sub>7</sub>. DXT5's color data is not premultiplied by alpha. Because DXT4/5 use an interpolated alpha scheme, they generally produce superior results for alpha (transparency) gradients than DXT2/3.