![http://imgs.xkcd.com/comics/standards.png](http://imgs.xkcd.com/comics/standards.png)

# Accepted standards and style guides

#### Front-end

- [JavaScript](https://github.com/Hotelsnl/standards/wiki/JavaScript)
- [Cascading Style Sheets and Pre-processors](https://github.com/Hotelsnl/standards/wiki/CSS)

#### Back-end

- [PHP: Hypertext Preprocessor](https://github.com/Hotelsnl/standards/wiki/PHP)

## PHP code style specification for CodeSniffer

### Installation

The code style specification is written for the CodeSniffer PEAR package so make
sure you have this package installed on your machine:

```bash
sudo pear install PHP_CodeSniffer
```

Once you have the CodeSniffer installed you should clone this github repository,
it does not have to be in a fixed location on your machine:

```bash
git clone git@github.com:Hotelsnl/standards.git
```

Now that all required files have been installed on your machine we need to
configure the CodeSniffer so it knows about your standards specification. We
assume that CodeSniffer is installed in it's default location, but it might be
somewhere else depending on your configuration and for the sake of simplicity we
assume that you cloned the github repository from the step above in your home
(~) directory:

```bash
cd /usr/share/php/PHP/CodeSniffer/Standards/
sudo ln -s ~/standards/Hotelsnl
```

The symlink is needed as CodeSniffer expects the standard to be in it's own
directory.

### IDE integration

#### VIM using the syntastic plugin

The CodeSniffer standard can easily be implemented using the Syntastic plugin
for VIM. The installation instructions for this plugin can be found at
[scrooloose/syntastic](https://github.com/scrooloose/syntastic)

If you have the Syntastic plugin installed you can add the CodeSniffer
configuration for it to your `.vimrc` file:

```viml
let g:syntastic_phpcs_conf="--standard=Hotelsnl --tab-width=2"
```

##### Note for Debian 6 users

If vim does not automatically show the codingstandards you can add this line to
yor .bash_profile

```bash
alias phpcs='phpcs --standard=Hotelsnl'
```

#### Komodo IDE

While this IDE is far less superior then VIM, it is also possible to integrate
the CodeSniffer with it. There is a extensive installation guide on the
[Drupal.org](http://drupal.org/node/1410310) site for it.

#### Netbeans

This IDE comes with a handy plugin and detailed installation guide which can be
found on the
[interwebz](http://www.amaxus.com/cms-blog/coding-standards-netbeans-php-codesniffer)

#### Other IDE's

I suggest your `rm -rf` it and [start](http://vim-adventures.com/)
[learning](http://vimcasts.org/) [VIM](http://www.vim.org/)

### Git integration

To prevent bad and invalid code from being committed in to the repositories you
need to install the `pre-commit` hook from this repository in to the
`.git/hooks` folder of your project. This needs to be done every time you clone
a repository.

To install the git hooks you can run the following commands in your terminal:

```bash
cd .git/hooks
ln -s ~/standards/Hotelsnl/hooks/pre-commit
```

To ignore the pre-commit hook you can append `--no-verify` to the commit command

If there is already pre-commit hook in your project you can append the contents
of the pre-commit hook to that file.
