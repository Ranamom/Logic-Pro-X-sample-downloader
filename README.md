
# lpx_links  
  
lpx_links is a utilty to get the direct download links for the additional sample/sound content for Logic Pro X.  
  
 - It gets the most current links  
 - Creates a text file with all the links in them.  
  
### 1. Download Link List  
  
Simply open the terminal and paste the command below.  
  
```sh  
cd ~/Downloads; curl -L -o master.zip https://github.com/chriswayg/Logic-Pro-X-sample-downloader/archive/refs/heads/master.zip ; unzip -oq master.zip ; cd Logic-Pro-X-sample-downloader-master ; ./lpx_links.rb
```  

### 2. Download Packages

To download I recomend using *aria2*   
- Simply download & install into `/usr/local/bin` - [aria2 ver1.35.0 installer](https://github.com/aria2/aria2/releases/download/release-1.35.0/aria2-1.35.0-osx-darwin.dmg)

- Then in the Terminal  
   
```sh  
# To only download the mandatory files (32 - about 1.6 GB)
cd ~/Downloads/ && aria2c --max-concurrent-downloads=10 --auto-file-renaming=false --continue=true --log=logic_download.log -i ~/Desktop/lpx_download_links/mandatory_download_links.txt --dir=logic_content

# To download all the packages (about 62 GB)
cd ~/Downloads/ && aria2c --max-concurrent-downloads=10 --auto-file-renaming=false --continue=true --log=logic_download.log -i ~/Desktop/lpx_download_links/all_download_links.txt --dir=logic_content
```

- --continue=true tells arai2 to continue/resume downloads.  
- -i is the path to the file with list of downloads.  
- -d is the path to where you want the downloaded files.   
     
  ![aria2 download example](https://github.com/davidteren/lpx_links/blob/master/images/aria2_example.png?raw=true)
  
### 3. Install Downloaded Packages
  
To install the downloaded packages use the following command:  
  
```sh  
cd Logic-Pro-X-sample-downloader-master && sudo ./install_pkgs.sh ~/Downloads/logic_content
```

### Version

0.0.7-1 - modified download_install.sh to only install the packages downloaded with aria2.

0.0.7 - added mandatory file list & refactor of code.  
- Includes Mandatory only list. Thanks to _Matteo Ceruti_ aka [Matatata](https://github.com/matatata) for the idea.  
  
0.0.6 - added version detection. Any version of Logic Pro X should work now.    
   
License  
----  
  
GNU General Public License, version 3 (GPL-3.0)  
(http://opensource.org/licenses/GPL-3.0)
