# FRET Simulator Setup

FRET's simulator needs another tool called "NuSMV" (pronounced 'noo Ess Em Vee' ), which needs to be downloaded before the simulator will work. NuSMV is available for Linux, Mac, and Windows.

## Installing NuSMV

1. Go to the [NuSMV downloads](https://nusmv.fbk.eu/downloads.html) page and download a `.tar.xz` file that is suitable for your operating system. The newest version of NuSMV (2.7.0 at the time of writing) should be fine

2. Move it to a sensible location (on Linux, I have a `bin` directory inside my home directory) and decompress it

3. Try running NuSMV to check that it works: run `NuSMV -h` from inside the `NuSMV-2.7.0-linux64/bin` directory. You should see a help page, which will look like this (with `Usage:  NuSMV [-h | -help] [options]* [input_file]` and a long list of switches at the bottom):

   ```bash
   *** This is NuSMV 2.7.0 (compiled on Fri Oct 25 17:21:01 2024)
   *** Enabled addons are: compass
   *** For more information on NuSMV see <http://nusmv.fbk.eu>
   *** or email to <nusmv-users@list.fbk.eu>.
   *** Please report bugs to <Please report bugs to <nusmv-users@fbk.eu>>
   
   *** Copyright (c) 2010-2024, Fondazione Bruno Kessler
   
   *** This version of NuSMV is linked to the CUDD library version 2.4.1
   *** Copyright (c) 1995-2004, Regents of the University of Colorado
   
   *** This version of NuSMV is linked to the MiniSat SAT solver. 
   *** See http://minisat.se/MiniSat.html
   *** Copyright (c) 2003-2006, Niklas Een, Niklas Sorensson
   *** Copyright (c) 2007-2010, Niklas Sorensson
   ```

4. Add the location of the binary (e.g. `/home/yourName/bin/NuSMV-2.7.0-linux64/bin`) and the location of FRET's simulator (e.g pathToFRET/fret/tools/LTLSIM/ltlsim-core/simulator) to your PATH environment variable (see the section below for step-by-step instructions)
5. Restart FRET and test the simulator
   - Open a requirement to Edit/Update it
   - Select "Semantics" below the the FRETISH text box
   - On the right-hand pane, select "Simulate" below the "Formalizations"
   - You should now see simulator
   - [FRET's manual](https://github.com/NASA-SW-VnV/fret/blob/master/fret-electron/docs/_media/UsingTheSimulator/ltlsim.md) gives instructions on how to use simulator





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

   

