# passman - A simple command line password manager

## Features

* Strong encryption via GPG
* Support for either public-key or symmetric encryption
* Add, get and delete passwords with simple commands
* Easy web browser / login forms support

## Usage

### Prerequisites and configuration

1. You have to have the following software installed an accessible on your system:

    [bash](http://www.gnu.org/software/bash/),
    [GnuPG](http://www.gnupg.org/),
    [dmenu](http://tools.suckless.org/dmenu/),
    [xdotool](http://www.semicomplete.com/projects/xdotool/),
    [pwgen](http://sourceforge.net/projects/pwgen/)

2. Create a plain password file with entries on each line like

        site<TAB>user<TAB>pass

    and encrypt it with one of the two following commands

        $ gpg --encrypt --recipient <gpg_identity> <plain_password_file>

    if you prefer to use your own private key or

        $ gpg --symmetric --cipher-algo AES256 <plain_password_file>

    if you want to use symmetric encryption without a private key.

3. Copy the file *config.dist* to *config* and modify the two variables $PASS_FILE and $GPG_IDENTITY to your needs. You may leave $GPG_IDENTITY empty. In this case symmetric encryption will be used.

4. For convenience set up a GPG-Agent which caches your GPG credentials for some time.

### Running

#### Adding a password

    $ passman add

#### Getting a password

    $ passman get <site>

#### Deleting a password

    $ passman del <site>

#### Filling forms (always display dmenu chooser)

    $ passman submitform

A dmenu dialog will pop up, let you chose the desired entry and enter the credentials via xdotool
in the form "user<TAB>password<RETURN>" or "password<RETURN>" if there is no user for an entry.

#### Filling forms (automatically try to match site key against current window name)

    $ passman autosubmitform

You may map this command to an easy system-wide keyboard shortcut to save time when filling out
browser login forms.

## License

This program is free software: you can redistribute it and/or modify
it under the terms of the GNU General Public License as published by
the Free Software Foundation, either version 3 of the License, or
(at your option) any later version.

This program is distributed in the hope that it will be useful,
but WITHOUT ANY WARRANTY; without even the implied warranty of
MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
GNU General Public License for more details.

You should have received a copy of the GNU General Public License
along with this program.  If not, see <http://www.gnu.org/licenses/>.