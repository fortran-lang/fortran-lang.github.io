# fortran-lang.org website

This repository contains the source for the fortran-lang.io website. 
It's derived from https://github.com/neovim/neovim.github.io.

## Contributing

* [CONTRIBUTING](./CONTRIBUTING.md): getting started and general guidance on contributing to <https://fortran-lang.org>

* [MINIBOOKS](./MINIBOOKS.md): how to write and structure a mini-book tutorial for the [Learn](https://fortran-lang.org/learn) section

* [PACKAGES](./PACKAGES.md): adding an entry to the [Package index](https://fortran-lang.org/packages)

* [TRANSLATING](./TRANSLATING.md): details on how to translate the webpage in a new language


## Setup

This assumes that you already have a recent Ruby with RubyGems.

For example on Ubuntu 18.04, do:
```
sudo apt install ruby-dev
```

### Installing Ruby gems

Install Bundler, either systemwide:

```
sudo gem install bundler
```

or for the current user:

```
gem install --user-install bundler
export PATH="$(ruby -e 'print Gem.user_dir')/bin:$PATH"
```

In the latter case, you might want to add the `PATH` update to `.bashrc` or your shell's equivalent.

To install the dependencies of this project, use Bundler:

```
bundle config set path '.bundle'
bundle install
```

### Serving locally

Execute the following command:

```
bundle exec jekyll serve --watch
```

Open `http://localhost:4000` to view the website.
