# ImageProcessing
Use Processing with image processing. [Processing](http://processing.org) is a simple yet powerful library / framework to work with images using Java. In this repo Processing is used mainly to create a number of popular image processing effects ( considering that it can be used in a great many of other ways ).

## Structure
This project was originally written in [Processing](http://processing.org), but has now been translated into pure Java.
For detailed compilation and running steps see **Compilation and Running** below.
The files described in the **Files** section together forms a simple GUI framework, while classes that implement the *Entry* interface mainly create the effects.

## Files
* **ImageProcessing.java**: The program entry, passes its events on to **UIManager.java**.
* **UIManager.java**: Respond to the events and provide a widgets management which allows users to have a simple GUI and control the image. It can be removed completely by moving the code to **ImageProcessing.java**, however that will make it difficult to rename the project, as there would be so many names to modify.
* **Entry.java**: Interface that describes an entry of an effect. Notice that there should be only one effect running at the same time.
* **Mouse.java**: Translator from *Processing Input Model* to the *Java Event Model*. ( okay just for fun ）
* **Registry.java**: Stores all the **Entries** and enables querying any one of them using a String key. ( well not so useful, it only saves me the effort to delete the code that initializes the other effects when I'm adding a new one )
* **Widget.java**: Contain interface **Widget** and implementations like **CheckWidget** and **RadioWidget** which represents the good-old checkbox and radiobox. **Widgets** are used as a simple GUI and work just like those we see on our computers every day.

## Images
There's no doubt that a image processing program needs images as input. There are some images in the repo for testing of my effects.
You can also copy your own images to the folder and modify **ImageProcessing.java** to watch the effects casted on them.
I decided not to describe the images a lot, only a few brief words. Some are photos of some *famous people* and others are down-samples of some pictures of mine.
btw *faster-than-anyone.png* is Chinese. Sorry.

## Effects ( under active development )
* Mosaic ( **EntryMosaic.java** ): The mosaic effect, generate a grid of shapes according to the color / grayscale of the corresponding point in the image. Can resize shapes using brightness and apply a fade-out effect. Shapes can be circular or rectangular.
* Halftone ( **EntryHalftone.java** ): The halftone effect, has modes that generate points along a rectangular grid or a set of concentric circles ( like in Adobe Photoshop ). Points can be circles or quads, and colors are sampled from either the original image or the grayscale image. ( effect actually look brighter than original 'cause the points are resized according to the brightness of the sampled point, so that's double brighter ). There's another wonderful effect under **EntryHalftone**, called *scatter* ( run the program and you'll see ). It actually works like a low-res image printed on a newspaper: the four basic types of ink ( black, magenta, cyan, yellow ) together forms the actual image. I found out that if I draw the four types of points with the same rotation angle the effect looks just like the *grid* version, however if I rotate each type a bit the effect would be awesome: under such a low resolution like this it can express such a exquisite final output. It's just kinda cool.
* Circles ( **EntryCircles.java** ): Forgive me for calling it in such a funny way, it's just I can't figure out a better name, or would anybody help me? Anyway, this effect generated shapes in different sizes and try to make them look like a black-or-white image together. Unfortunately there're a few parameters in the program that must be artificially adjusted for the best effect according to the image. The ones in the code works on *faster-than-anyone.png*. Shapes can be circles, quads, hexagons or texts. You can modify the text content ( currently letters of "SIMPLE" ) and font ( currently "DIN Black", in case you have had it installed ).
* Fill ( **EntryFill.java** ): Another terrible name, hope I wake up the next morning and come up with a better one. This one works in many ways like the *Circles* Entry, also filling in an black-or-white image with many identical shapes ( or letters ) of different sizes. The real difference is, that this one trys to make the shape as large as it can get ( as the image allows ) while attempting to add a new shape, which makes the coverage of the shapes to the original image larger ( compared to *Circles* ) and look better.

## Compilation and Running
The following steps will guide you to the output result of the program:
1. Clone the whole repo.
2. Create a new project in your own IDE. ( Mine is IntelliJ IDEA )
3. Install [Processing](http://processing.org)
4. Add Processing core libraries to your classpath. Should be under **/code/library** under the installation path of Processing, mine is ( 64-bit windows) **C:\Program Files\Processing\code\library**. Add all JARs or simply the whole directory.
5. Compile the source files. ( Of course you should first hava Java installed )
6. Run Main.class
7. Have a cup of coffee and enjoy.

## Others
This projects compiles and runs under Processing 3.0.2 and java 1.8. 
