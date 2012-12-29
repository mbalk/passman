# passman - A simple command line password manager

## Features

* Strong encryption via GPG
* Add, get and delete passwords with simple commands
* Easy web browser / login forms support via *dmenu* and *xdotool*

## Usage

### Prerequisites and configuration

1. You have to have the following software installed an accessible on your system:

    [bash](http://www.gnu.org/software/bash/),
    [GnuPG](http://www.gnupg.org/),
    [dmenu](http://tools.suckless.org/dmenu/),
    [xdotool](http://www.semicomplete.com/projects/xdotool/),
    [pwgen](http://sourceforge.net/projects/pwgen/)

2. Create a plain password file with entries on each line like

        site,user,pass

    and encrypt it with the following command

        $ gpg -e -r <gpg_identity> <password_file>

3. Modify the two variables $PASSFILE and $GPG_IDENTITY in the *passman* script to your needs.

### Running

#### Adding a password

* With existing password (user may be empty)

        $ passman add <site> <user> <password>

* Without existing password (password will be generated by pwgen)

        $ passman add <site> <user>

#### Getting a password

    $ passman get <site>

#### Filling forms

    $ passman fill

A dmenu dialog will pop up, let you chose the desired entry and enter the credentials via xdotool
in the form "user<tab>password<enter>" or "password<enter>" if there is no user for an entry.

## License

TrayNotify is free software: you can redistribute it and/or modify
it under the terms of the GNU General Public License as published by
the Free Software Foundation, either version 3 of the License, or
(at your option) any later version.

TrayNotify is distributed in the hope that it will be useful,
but WITHOUT ANY WARRANTY; without even the implied warranty of
MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
GNU General Public License for more details.

You should have received a copy of the GNU General Public License
along with TrayNotify.  If not, see <http://www.gnu.org/licenses/>.