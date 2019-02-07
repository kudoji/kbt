# kbt

kbt is a simple backup tool built with bash.

The tool runs on Mac OS and Linux based distributions.

## configuration

kbt creates the following directory structure at first run:
* $HOME/.kbt/local/mirror
* $HOME/.kbt/local/update
* $HOME/.kbt/lan/mirror
* $HOME/.kbt/lan/update

**mirror** folders
    
    keep settings for mirror backups, which means that destination folder will be identical to the source.

Inside the folder you need to create symlinks to the folders you want to be backed up.

**update** folders

    destination will be updated to the source state with keeping old files that are not more in the source.

Inside the folder you need to create symlinks to the folders you want to be backed up.

#### $HOME/.kbt/local

    local folder keeps settings for the local backups, e.g. from you main drive to an inserted usb drive

Inside the folder symlink named "**dest**" to the destination directory must be created in case of using local backup option(s).

#### $HOME/.kbt/lan

    lan folder keeps settings for the lan backups. E.g.: from the current machine to the another over network

Inside the folder file named "**config.lan**" must be created in case of using lan backup(s). The file has simple structure:
* first line (mandatory): [user_name]@[ip]. E.g.: backup@192.168.0.1
* second line (optional) specifies port number to ssh remote server, 22 will be used if line is omitted.

## usage

When executed kbt shows description and menu with user prompt.
The menu looks as follows:

1. sync test & exit
2. sync & exit
3. lan sync test & exit
4. lan sync & exit

        test options recommended to run first to see what script will do when commit options is selected (2 or 4)

## performance issues during backup over network

Current implementation uses ssh which might be slow in case of backuping huge files.
If it is a case, using nfs mount is recommended with local option.

Happy backuping!