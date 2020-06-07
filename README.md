## Some Useful IDL Libraries:

| Name                                                         | Function                                             |
| ------------------------------------------------------------ | ---------------------------------------------------- |
| [CLEAR](https://climate.web.runbox.net/idl_lib/pro/clear.pro) | This procedure clears the active IDL display window. |
| [CLS](https://climate.web.runbox.net/idl_lib/pro/cls.pro)    | This procedure clears the IDL terminal window.       |

**Quick Installtion Commands**  
Run commands below for installing above libraries:
```shell
idl_libs=`readlink \`which idl\``
idl_libs="${idl_libs/\/bin\/idl/"/lib"}"

sudo wget https://raw.githubusercontent.com/Dishendramishra/idl_tutorial/master/libraries/clear.pro -P $idl_libs
sudo wget https://raw.githubusercontent.com/Dishendramishra/idl_tutorial/master/libraries/cls.pro -P $idl_libs
unset idl_libs
```

For more check **Dáithí** libraries https://climate.web.runbox.net/idl_lib/index.html



# Installing IDL

- ### **On Linux**

```shell
#Fixing  libXp.so.6
sudo apt install -y libxpm4 imagemagick
sudo ln -s /usr/lib/x86_64-linux-gnu/libXpm.so.4.11.0 \
/usr/lib/x86_64-linux-gnu/libXp.so.6

cd
gdown --id 132FL4KwI7VWdzrw2bVc4vxqeRXuQZaJN
gdown --id 1HvQAtnpxGbcAe6yqUHc3hFAFgwM0RI9i
sudo mkdir /usr/local/itt      
sudo tar -xvf ./idl71linux.x86.tar.gz --directory /usr/local/itt/
cd /usr/local/itt
sudo /usr/local/itt/install
cd
sudo mv ./license.dat /usr/local/itt/license/
```

<br>

- ### On Mac

```shell
brew cask install xquartz

cd
gdoen --id 1RBBZztZ3_W92uMUySzQ5RCAOYFB6uWiD
sudo tar -xvf idl_mac.tar --directory /usr/local/
cd /usr/local/itt
sudo chmod +x /usr/local/itt/install
sudo /usr/local/itt/install
```



:warning:**Fixing zlib issue**

If you encounter following error:

<img src="./images/zlib_error.png" style="zoom:50%;" />

The execute following command to fix it.

```shell
sudo rm -rf /usr/local/itt/idl706/bin/bin.darwin.x86_64/libz.1.dylib
```

---

<br>

### **Installing Libraries**

I **strongly recommend** these libraries, these commands works on both Linux and Mac.

```shell
idl_libs=`readlink \`which idl\``
idl_libs="${idl_libs/\/bin\/idl/"/lib"}"

sudo git clone https://github.com/Dishendramishra/coyote $idl_libs/coyote
sudo git clone https://github.com/Dishendramishra/IDLAstro $idl_libs/astron
sudo wget https://raw.githubusercontent.com/Dishendramishra/idl_tutorial/master/libraries/clear.pro -P $idl_libs
sudo wget https://raw.githubusercontent.com/Dishendramishra/idl_tutorial/master/libraries/cls.pro -P $idl_libs
unset idl_libs
```



# **Installing Exofastv2**

```shell
cd $HOME/idl
git clone https://github.com/Dishendramishra/EXOFASTv2
```



Then execute following commands to define necessary paths in your `bash_profile` 

```shell
echo -e '\n' >> ~/.bash_profile
echo '# if IDL_PATH is not defined, add EXOFAST_PATH and subdirectories to the default IDL path' >> ~/.bash_profile
echo 'if [ -z "$IDL_PATH" ]; then' >> ~/.bash_profile
echo 'IDL_PATH="<IDL_DEFAULT>:+${EXOFAST_PATH}" ; export IDL_PATH' >> ~/.bash_profile
echo 'else' >> ~/.bash_profile
echo '# otherwise, append EXOFAST_PATH and all subdirectories to your IDL_PATH' >> ~/.bash_profile
echo 'IDL_PATH="${IDL_PATH}:+${EXOFAST_PATH}" ; export IDL_PATH' >> ~/.bash_profile
echo 'fi' >> ~/.bash_profile

```

:warning: If you are another shell like `oh-my-zsh` then execute command given below:

```shell
echo "\n" >> ~/.zshrc
echo "source ~/.bash_profile" >>  ~/.zshrc
```

 

**Testing exofastv2**

```shell
cd $EXOFAST_PATH/examples/hat3
idl -e "fithat3"
```