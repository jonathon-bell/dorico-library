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
* **main**: A snapshot of the default library that ships with Dorico. Useful as a reference to diff against and to see what has changed.
* **jazz**: Extends **main** with a style based on the _Rhapsody_ SMuFL font family by [NorFonts](https://norfont.com/en/product/rhapsody-smufl-font//). This has a handwritten look that mimics the Real Book.

## The 'jazz' branch

A set of project templates based on the _Rhapsody_ SMuFL font family by [NorFonts](https://norfont.com/en/product/rhapsody-smufl-font//). This has a hand written look that mimics the Real Book.

### Templates

The following project templates were first created in Dorico Version 6.1.10.6078 (Oct 8 2025).

#### Empty

An empty project template capturing the settings that comprise the 'jazz' house style. This template is only used only to create other project templates.

To re-create it from scratch:
* Open Dorico
* **File | New** to create an empty project
* **File | Save As...** to save as "~/Downloads/Empty.dorico"
* **Library | Instruments..."** to create a _Melody_ instrument (the name "Lead" is already taken):
  * Copy the _Piano_ instrument
  * Change its names to "Melody", "Mel", "Melody", and "Mel"
  * Change Families to Sketch
  * Change Number of staves to 1
  * Change Rhythm section instrument to ❎
  * Enable the ⭐️ button to **Save as Default** (i.e. add to userlibrary.xml)
* **Add Single Payer** and select *Melody* as its instrument
* Modify the following settings in the order listed below:

Setting                                   | Value
------------------------------------------|------------------------------------
**Dorico \| Preferences...**
Colors » Background Colors » Write mode   | Solid Stone
Colors » Background Colors » Engrave mode | Solid Stone
General » Default paper size type         | North American
General » Default text font family        | Rhapsody Alpha
**Library**
Music Fonts                               | Rhapsody (❎ fonts ✅ engraving options)
**Library \| Font Styles...**
Chord Symbols Alt Bass Sep Font           | Rhapsody Alpha         12.0
Chord Symbols Font                        | Rhapsody Alpha         18.0
Chord Symbols Music Text Font             | Rhapsody Text          18.0
Default Music Font                        | Rhapsody
Default Music Text Font                   | Rhapsody Text
Default Text Font                         | Rhapsody Alpha
Tablature Numbers Font                    | Rhapsody Alpha
**Library \| Paragraph Styles...**
Default Text                              | Rhapsody Alpha         12.0
Artist                                    | Rhapsody Alpha         10.0
Print Date                                | Rhapsody Alpha          8.0
Layout Name                               | Rhapsody Alpha         14.0 ❎ Border
Rehearsal Marks Text                      | Rhapsody Alpha Bold    14.0 ✅ Border
**Library \| Character Styles...**
Metronome Mark Music Text                 | Rhapsody               7/4
Music Text                                | Rhapsody Text
**Library \| Layout Options...**
Repeat Markers » Default placement        | Below staff
Page Setup     » Page Size » Size         | Letter
Page Setup     » Page margins » Top       | 15mm
Page Setup     » Page margins » Bottom    | 10mm
Page Setup     » Page margins » Left      | 15mm
Page Setup     » Page margins » Right     | 15mm
**Library \| Engraving Options...**
Chord Symbols » Chord Symbol Preset       | Brandt-Roemer
Barline Joins » Barline at end of system… | Double barline
Barlines » Wings on repeat barlines       | Show wings
Rests » Multi-bar Rests » Bar count for...| No bar count
**Library \| Playback Options...**
Metronome Click » Click Sound             | Wood Block
Note Dynamics » Marcato » Increase by     | 1.0
**File \| Project Info...**
Title                                     |
Copyist                                   | Jonathon Bell
Copyright                                 | Copyright © {@projectcompositionyear@} {@projectcomposer@}
Other information                         | Cambridge {@projectcompositionyear@}
Generate preview ...                      | ❎
Resolve Markdown ...                      | ❎

* **Save as Default** each modification where appropriate:
  * For font related settings, enable the selected item's ⭐️ button
  * For _Options..._ dialogs, click the **Save as Default** button in the bottom left hand corner of the dialog
* Install the **Jazz** page template set:
  * Switch to **Engraving Mode**
  * Import the custom page template set from an existing project
  * Apply the imported set to the Full Score layout
* Remove the _Melody_ player and its part layout
* **File | Save As Project Template...** to save the project as a template:
  * ❎ Preserve existing flows
  * ✅ Preserve Project info

#### Guitar

A project template for creating exercises and studies for the 6 string guitar.

Created from the Empty template.

To re-create it from scratch:
* Open Dorico
* **File | New Project From Template** and choose the "Wolery/Empty" template.
* **File | Save As...** to save as "~/Downloads/Guitar.dorico"
* **Add Single Payer** and select *Jazz Guitar* as its instrument
* In **Setup Mode**:
  * Rename the player "Guitar"
  * Remove the "Full Score" layout
* Modify the following settings in the order listed below:

Setting                                      | Value
---------------------------------------------|------------------------------------
**Library \| Layout Options...**
Players » Fretted Instruments » Guitar       | Notation and tablature
Players » Bar Rests and ... » Consolidate    | None
Staves and Systems » Indent first system ... | 0 spaces
**File \| Project Info...**
Title                                        |
Composer                                     | Jonathon Bell

* In **Engraving Mode** select the **Jazz** Page Template Set and apply it to the _Guitar_ part layout.

* **File | Save As Project Template...** to save the project as a template:
  * ✅ Preserve existing flows
  * ❎ Preserve Project info

#### Lead Sheet

A project template for creating lead sheets.

Created from the Empty template.

To re-create it from scratch:
* Open Dorico
* **File | New Project From Template** and choose the "Wolery/Empty" template.
* **File | Save As...** to save as "~/Downloads/Lead Sheet.dorico"
* **Library | Instruments..."** to create a _Melody_ instrument (the name "Lead" is already taken):
  * Copy the _Piano_ instrument
  * Change its names to "Melody", "Mel", "Melody", and "Mel"
  * Change Number of staves to 1
* **Add Single Payer** and select *Melody* as its instrument
* **Add Single Payer** and select *Jazz Guitar* as its instrument
* In **Setup Mode**:
  * Add a layout "C"  to the _Melody_ player
  * Add a layout "B♭" to the _Melody_ player and transpose to B♭3
  * Add a layout "E♭" to the _Melody_ player and transpose to E♭4
  * Add    the _Melody_ player to the flow _Head_
  * Remove the _Guitar_ player to the flow _Head_
  * Rename the Jazz Guitar player "Guitar"
  * Remove the "Full Score" layout
  * Rename the intial flow "Head"
* Modify the following settings in the order listed below:

Setting                                   | Value
------------------------------------------|------------------------------------
**Library \| Layout Options...(guitar)**
Players » Fretted Instruments Guitar      | Notation and tablature
**Library \| Layout Options...(all)**
Players » Bar rests and ... » Consolidate | None
Casting Off » Fixed bars per system       | 4
**File \| Project Info...**
Title                                     |
Composer                                  | Jonathon Bell

* In **Engraving Mode** select the **Jazz** Page Template Set and apply it to all part layouts.

* **File | Save As Project Template...** to save the project as a template:
  * ✅ Preserve existing flows
  * ❎ Preserve Project info

## Contributing

This is a personal project maintained by [Jonathon Bell](https://github.com/jonathon-bell).

## License

The contents of this repository are made available under the MIT License. See [here](license.md) for details.
