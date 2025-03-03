# FRET Realisability Setup


FRET's realisability checker is ***not supported in Windows***
```
Note : Realizability checking is not currently supported in Microsoft Windows.
```

This guide shows you how to install the dependencies to make FRET's realisability checker work. It uses one of the four options suggested in FRET's manual page about [Realisabiltiy Checking](https://github.com/NASA-SW-VnV/fret/blob/master/fret-electron/docs/_media/exports/realizabilityManual.md)

## Installing FRET and the required tools for Realisability Checking

The steps below assume that you have not got FRET already. If you have already installed FRET and it runs ok, jump to step 4.

1. clone fret from [github](https://github.com/NASA-SW-VnV/fret.git)
2. Install fret (remember to check the version of Node matches the dependencies) ``npm run fret-install` from inside the `fret/fret-electron` directory
3. Check that fret will run `npm start` from inside the `fret/fret-electron` directory

4. Install Z3 (a theorem prover from Microsoft Research):
   * download a zip file containing a [stable release](https://github.com/Z3Prover/z3/releases) of Z3 that is suitable for your CPU/Operating System
   * extract the zip
   * add the location of the binary (e.g. `/home/yourName/bin/z3-4.13.4-x64-glibc-2.35/bin`) to your PATH environment variable (see the section below for step-by-step instructions)

5. Try running Z3 to check it works: `./z3 -h` from inside `z3-4.13.4-x64-glibc-2.35/bin`, this should show you the z3 help page

6. Install Kind2 (a model checker that uses Z3):
   * You can install it as described in their [README](https://github.com/kind2-mc/kind2/blob/develop/README.rst)
   * download a `.tar.gz` file from their [releases](https://github.com/kind2-mc/kind2/releases/tag/v2.1.1) page (make sure to use v2.1.1 as I've had some problems with newer versions of Kind2)
   * decompress the `.tar.gz` file
   * add the location of the binary (e.g. `/home/yourName/bin/kind2-v2.1.1-linux-x86_64`) to your PATH environment variable (see the section below for step-by-step instructions)

7. Try running Kind2 to check it works: `/kind2 --version` from inside `kind2-v2.1.1-linux-x86_64`, this will probably show something like 
```
 kind2 v2.1.1
```
8. Make sure that your path is reloaded, by either logging out and back in, or running `source ~/.profile` (if you have your PATH variable in `.profile`)
9. Finally, run FRET, open the Analysis Portal, select "Realizability" and choose a project. The explanation for how to _use_ the Realisability Checker are in the [FRET manual](https://github.com/NASA-SW-VnV/fret/blob/master/fret-electron/docs/_media/exports/realizabilityManual.md)


## Adding to your PATH environment variable

Below I have used `yourName` to stand in for your username, you should replace it with your actual username.

### Linux/Unix


1. Open your $HOME folder (i.e. the folder that is your username)
2. Go to View → Show Hidden Files or press `Ctrl + H` on the keyboard
3. Right click on `.profile` and select `Open With Text Editor`
4. Scroll to the bottom of the file and add (for example) `PATH="$PATH:/home/yourName/dir"` to add the `dir` directory in your home directory to the path
5. Save
6. Either:

   * Log out and log back in to apply changes (loads `.profile`), or;
   * (if you're working in a terminal window) type `source ~/.profile` and press enter

### MacOs

1. Open a terminal and run `sudo nano /etc/paths` to open the `paths` file in `nano`
2. At the bottom of the file, add `/usr/yourName/dir` to add the `dir` directory in your home directory to the path
3. Press Control + x on your keyboard to quit, pressing y to save the changes
4. Close the terminal and open a new one, this will reload the path. To check it's worked, run `echo $PATH` and check that your new directory is shown.

### Windows 

For Windows 10/11 (un-tested by me)

1. open the Start menu and type "environment properties", then press Enter
2. In the 'System Properties' window, you should be on the 'Advanced' tab; click the "Environment Variables" button at the bottom
3. Find the "Path" variable in the list, and click "Edit"
4. Add (for example) `:C:\yourName\dir` to the "Variable Value", which adds the `dir` folder in your home folder on the C drive to your path; Click "OK"
