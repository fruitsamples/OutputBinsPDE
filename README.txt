The OutputBinsPDE project demonstrates how to write a Cocoa PDE that supports
PPD features and that runs on Mac OS X versions 10.5 and later.  This version
does not contain code that demonstrates proper runtime handling in Mac OS X
version 10.4; the Leopard Developer Tools contains such a version.


INSTALLATION

To build and install debug 3-way fat:

    sudo xcodebuild -configuration Debug DSTROOT=/ UNSTRIPPED_PRODUCT=YES \
        install RC_ARCHS="ppc i386 x86_64"

To build and install release 3-way fat:

    sudo xcodebuild -configuration Release DSTROOT=/ \
        install RC_ARCHS="ppc i386 x86_64"

Either of these installs the OutputBinsPDE plugin and a PPD file that
references it.  The PPD is for a generic printer model called "OutputBins PDE
test".  This is a PPD for a PostScript printer but there is no reason it has to
be. 

To test the OutputBinsPDE you have to create a print queue for it.  Browse to a
PostScript printer and assign this PPD manually. Just choose the printer and select
"Select Printer Software..." from the "Print Using:" popup to choose a PPD by model.  
You can find the relevant PPD by typing "Output" into the text search field below
the title of the PPDPicker window. This will show you the PPD for the "PostScript Printer
Manufacturer OutputBins PDE test" printer model. Click on that PPD and choose Add.

NOTES

When designing your own PDEs, please follow the HI guidelines published by
Apple to ensure that your user interface looks and behaves like the native
system user interfaces.  These guidelines are available online at:

    http://developer.apple.com/documentation/UserExperience/Conceptual/AppleHIGuidelines

PDEs should be designed so they are no larger than 420 pixels wide and 320
lines high.  Larger panes will cause unnecessary resizing and may be clipped
on systems with smaller displays - remember to test your user interfaces on
displays set to a resolution of 1024x768!

Finally, make sure that your UI controls use the same strings as your PPD
files, since many auto-generated error messages use the PPD strings.  If the
user interface and PPD file do not use the same strings, users may become
confused and/or frustrated!
