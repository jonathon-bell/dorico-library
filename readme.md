# 🎼 Dorico Library

Source code for my Dorico User Library.

## Usage

Clone the repo into the Dorico application support directory (macOS):

    cd ~/Library/Application\ Support/Steinberg/Dorico\ 6
    git init                      # because the directory will not be empty
    git remote add "origin" git@github.com:jonathon-bell/dorico-library.git
    git checkout jazz
    git pull

Branches describe different 'house styles':
* **main**: A snapshot of the default library that ships with Dorico. Useful as a reference to diff against and so see what has changed.
* **jazz**: Extends **main** with a style based on the _Rhapsody_ SMuFL font famiily by [NorFonts](https://norfont.com/en/product/rhapsody-smufl-font//). This has a hand written look that mimics the Real Book.

## Contributing

This is a personal project maintained by [Jonathon Bell](https://github.com/jonathon-bell).

## License

The contents of this repository are made available under the MIT License. See [here](license.md) for details.
