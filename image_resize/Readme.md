# Mogrify Installation and Usage on MAC

## Installation

To install `mogrify` on a Mac, you need to install ImageMagick, as `mogrify` is a part of the ImageMagick suite. You can use Homebrew to install ImageMagick:

1. Open Terminal.
2. Install Homebrew if you haven't already:

   ```bash
   /bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
   ```

3. Install ImageMagick using Homebrew:

   ```bash
   brew install imagemagick
   ```

## Usage

Once ImageMagick is installed, you can use the `mogrify` command to batch process images. Here are some common use cases:

1. **Resize Images**: To resize all `.jpg` images in the current directory to a width of 800 pixels:

   ```bash
   mogrify -resize 800 *.jpg
   ```

2. **Convert Image Format**: To convert all `.png` images in the current directory to `.jpg` format:

   ```bash
   mogrify -format jpg *.png
   ```

3. **Compress Images**: To compress all `.jpg` images in the current directory:

   ```bash
   mogrify -quality 85 *.jpg
   ```

4. **Rotate Images**: To rotate all `.jpg` images in the current directory by 90 degrees:

   ```bash
   mogrify -rotate 90 *.jpg
   ```

For more options and detailed usage, refer to the [ImageMagick documentation](https://imagemagick.org/script/mogrify.php).

5. **Complex Operation**: Define working directory and resize all images in the directory and subdirectories to 800 pixels:

   ```bash
   # Set current user's Pictures directory as the working directory
   mypath=~/Pictures/original
   ```

   ```bash
   cd $mypath
   mkdir -p $mypath/600


   mogrify -path $mypath/600 -format webp -resize 600x600 -background white -gravity center -extent 600x600 *.*
   ```

   I need a transparent background image, so I used the following command:

   ```bash
   mogrify -path $mypath/600 -format webp -resize 600x600 -background none -gravity center -extent 600x600 *.*
   ```

   I need to rersize to same width independently from the height, but keep the image ratio, so I used the following command:

   ```bash
   mogrify -path $mypath/600 -format webp -resize 600x -background none -gravity center -extent 600x *.*
   ```
