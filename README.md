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
