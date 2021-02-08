### **Welcome!!!**

For any questions, programs, or accounts that aren't addressed here, look at the other tabs in the Wiki of the [**getting_started**](https://bitbucket.org/cmelab/getting-started/wiki/Home) repository. 

#### Installing Homebrew
* Let's install [Homebrew](https://brew.sh), the missing package for macOS! This will make our lives a lot easier when trying to install other things later. Run the below command

      `/usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"`

      If you are having issues with Homebrew or something isn't downloading correctly, `brew doctor` is a great command to check and see what is going on. You may also need to do `brew upgrade` if things still aren't working.

* Now install some much needed packages!
    * `brew install git`
    * `brew install make`
	* `brew install cmake`
    * `brew install build-essential`
    * `brew install rlwrap`
    * `brew install wget`

* It can be helpful to organize all of the repositories we will clone, so we can make a directory called Projects
	* `cd ~`
	* `mkdir Projects`
	* `cd Projects`

* Since git is installed now, clone [**cme_utils**](git@github.com:cmelab/cmeutils.git) and [**getting_started**](git@github.com:cmelab/getting-started.git) from Github since they have important settings that we use to run our simulations and code.

* This part is more optional than required but our **getting_started config_files** folder has some defaults already set up for your bash_profile, vmdrc (which you will download in a moment), and vimrc and you can follow the below commands to copy them into your own files. 
    * `cd getting-started/config_files/`
    * `cp bash_profile ~/.bash_profile`
    * `source ~/.bash_profile`
    * `cp vmdrc ~/.vmdrc`
    * `cp vimrc ~/.vimrc`

* Install [VMD](https://www.ks.uiuc.edu/Development/Download/download.cgi?PackageName=VMD)! This allows you to visualize the gsd files we make when running simulations. You will have to make an account to do this. 
	* On the VMD download webpage, you'll notice a lot of different download options. These are for different versions of VMD as well as different operating systems
	* Download VMD version 1.9.4.
	* In total, there are 3 different options for Mac based operating systems:
		* If you're using a mac with an M1 chip, download the version designed for ARM processors
		* If you're using a non M1 mac (Intel), download the version designed for x86. You can choose between a 32 bit and 64 bit version depending on your current MacOS version. 

* Once VMD is installed we need to install a plugin that allows VMD to open .gsd files:
    * `cd ~/Projects`
	* `git clone https://github.com/mphoward/gsd-vmd` ([github link](https://github.com/mphoward/gsd-vmd))
    * `cd gsd-vmd`
    * `mkdir build && cd build`
    * `cmake ..`
    * `make install`

* Let's make sure VMD can open successfully. Typically, you will use the command line in a terminal window to open VMD. This requires that an alias is set in your `.bash_profile`
	* If you followed the instructions above in setting up the getting started config files, the alias might already be created.
	* Run `which vmd` in the terminal window. You should see something like `vmd: aliased to rlwrap /Applications/VMD\ 1.9.4a51-x86_64-Rev9.app/Contents/MacOS/startup.command`
	* If you DO see this, then try opening vmd from command line by running the command `vmd`. If VMD opens (3 windows total) then the alias is correctly set up.
		* If VMD does not open, double check the path of your VMD installation and the path given in the alias printed out; they have to match exactly. 
	* If you DON'T see this, then the `vmd` alias still needs to be added to your `.bash_profile`. You can add it yourself, or copy 


* Download Miniconda! For more extensive instructions, visit the **Installing the Frequently-Used Programs for CME-Lab** tab in the wiki of the [**getting_started**](https://bitbucket.org/cmelab/getting-started/src/master/) repository. 
    * `cd ~/Downloads/`
    * `wget https://repo.anaconda.com/miniconda/Miniconda3-latest-MacOSX-x86_64.sh`
    * `bash Miniconda3-latest-MacOSX-x86_64.sh`
    * `conda source`

* Now we can install programs with conda! Some of these might be repeats so remove any of them that you don't want to install again.
    * `conda install -c mosdef -c omnia mbuild foyer --only-deps`
    * `conda install -c conda-forge -c mosdef -c omnia hoomd jupyter numpy matplotlib freud gsd`
    * `conda install -c conda-forge signac signac-flow`

#### **RECOMMENDED:** If you don't want to install all these things for all projects you will be working on, you can create conda environments to reflect what you want each of them to do.
`conda create --name <new environment name>` --> creates a new environment  
`conda activate <environment name>` --> puts you in your environment  
`conda deactivate` --> takes you out of your environment  
`conda env remove -n <environment name>` --> removes an environment  
`conda create --name <new environment name> --clone <the one you are cloning>` --> copies one environment into another

#### **NOTE:** If you haven't used vim before as an editor, you can do a tutorial with the command `vimtutor` which will help you understand how to type in files!
