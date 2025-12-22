# 🎼 Dorico Library

Project templates and documentation for my Dorico house styles.

## Philosophy

Dorico’s exported library format (`.doricolib`) and internal XML representations cannot be treated as a composable or mergeable codebase. While these text files appear versionable at first glance, in practice they are:

* not well documented by Steinberg
* opaque in intent
* order-dependent
* sensitive to save / reopen cycles
* prone to implementation leakage
* incomplete with respect to font-driven, derived, or recomputed settings

Instead, I version **project** (`.dorico`) files rather than attempting to manage or diff their internal data. The project file is treated as a stable containment boundary, not as a transparent source representation.

From this follow the guiding principles:

* Branches represent complete stylistic universes, not lines of development.
* No branch is merged into another. History is linear within a style but isolated across styles.
* Declarative documentation is the source of truth, not Dorico’s serialized output.
* Project templates are products, not sources.
* One “oracle” project per style captures intentional engraving decisions and evolves slowly.

I use Git as a _snapshot selector_, not as a collaborative version control system.

I use Git tags to mark stable milestones in the evolution of a house style or template set. A tag denotes a point at which the visual appearance, engraving conventions, and layout behavior are considered internally consistent and suitable for reuse or rollback. Tags are not expected to be frequent, nor do they imply compatibility between tagged versions; they simply identify known-good states that can be returned to exactly. Day-to-day experimentation occurs on branches, while tags serve as durable reference points.

## Usage

Clone the repo into the Dorico application support directory. For macOS:

    cd ~/Library/Application\ Support/Steinberg/Dorico\ 6
    git init
    git remote add "origin" git@github.com:jonathon-bell/dorico-library.git
    git checkout jazz
    git pull

The `init` + `remote` sequence works around Git's reluctance to clone a repo into a directory that is not empty.

Branches describe different house styles:
* **main**: A snapshot of the default library that ships with Dorico. Useful as a reference to diff against and see what has changed.
* **jazz**: Extends **main** with a style based on the _Rhapsody_ SMuFL font family by [NorFonts](https://norfont.com/en/product/rhapsody-smufl-font//). This has a handwritten appearance that mimics that of the Real Book.

## Contributing

This is a personal project maintained by [Jonathon Bell](https://github.com/jonathon-bell).

## License

The contents of this repository are made available under the MIT License. See [here](license.md) for details.
