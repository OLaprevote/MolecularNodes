---
title: "Installation"
editor: visual
---

To install molecular nodes, download the [latest release](https://github.com/BradyAJohnston/MolecularNodes/releases) from the github releases page. Ensure that you have a version of Molecular Nodes that matches the version of Blender you have installed.

::: callout-caution
## Blender Version 3.4

Molecular Nodes `2.0` is only compatible with Blender 3.4 & above.

There are earlier versions of MN which are compatible with earlier versions of Blender, but these are no longer being developed or maintained and it is highly recommended that you use the most recent Blender and Molecular Nodes.

Details for each release are available on the [releases page](https://github.com/BradyAJohnston/MolecularNodes/releases).
:::

## Downloading Requirements

1.  Download and install Blender 3.4 from [blender.org](https://www.blender.org/download/).

2.  Download the latest MolecularNodes from the [MolecularNodes Releases Page](https://github.com/BradyAJohnston/MolecularNodes/releases/).

::: callout-warning
### Download the Right Thing

Importantly do not download the entire MolecularNodes GitHub repo and try to install that. Download the bundled release from the [release page](https://github.com/BradyAJohnston/MolecularNodes/releases) and install that with Blender.

![](https://imgur.com/3thv8YM)
:::

## Installing the Addon

### Open a New Session of Blender

::: callout-warning
### Administrator

If you are on Windows, you may need to run Blender as Administrator to install additional dependencies successfully.
:::

### Open Preferences Panel

> Click 'Edit' -\> 'Preferences' or press <kbd>Cmd</kbd> + <kbd> ,</kbd> on Mac.

![](https://imgur.com/Mv8tHMC)

### Click 'Install' on the Addon Page

> Click on the 'Add-ons\` tab on the middle left, then the 'Install' button on the top right.

![](https://imgur.com/6ri9FUl)

### Select `MolecularNodes_X.zip`

> The `X`'s will be the current version number of the add-on.

::: callout-warning
### `.zip` Files

When downloading on MacOS with Safari, it automatically unzips the file into a `MolecularNodes` folder. This is extremely unhelpful as Blender requires the `.zip` file to install the addon. Either download with a different browser, or compress the folder again to `MolecularNodes.zip`.
:::

![](https://imgur.com/uFWZP42)

### Enable the Add-on

If the preferences panel doesn't automatically show the installed add-on, search for the add-on to find it. Tick the box in the upper-left corner to enable it.

![](https://imgur.com/8vVmzVt)

The nodes are now enabled and available inside of Geometry Nodes in Blender. However to be able to download and parse structure files, additional python libraries will need to be installed via `pip` in the next step.

## Installing `Biotite` & `MDAnalysis`

There are two additional python packages which are required for MolecularNodes to function.

[`Biotite`](https://biotite-python.org) handles the majority of the structure file parsing. [`MDAnalysis`](https://www.mdanalysis.org/) handles the reading of molecular dynamics trajectories.

To install both packages, it should be a single button press inside of Blender, unless you are on an M1 or M2 Mac.

::: {.callout-warning collapse="true"}
## MacOS M1 & M2

Blender's bundled python is unable to install python packages that require compilation on the user's machine. Currently, MDAnalysis is missing a pre-compiled `.whl` to install, and thus installation will fail on M1 & M2 machines. You can download and pre-compile these packages on your machine yourself, following the below instructions.

This is the current fix for M1 / M2 machines, but will be fixed in [future releases](https://github.com/BradyAJohnston/MolecularNodes/issues/108#issuecomment-1467914853).

In short:

1.  Install [miniconda](https://docs.conda.io/en/latest/miniconda.html)
2.  Download and build the required pacakges for your system
```bash
mkdir ~/MDAnalysis-wheel
cd MDAnalysis-wheel
conda create -n wheel-builder python=3.10 cython
conda activate wheel-builder
python -m pip wheel MDAnalysis==2.2.0 --cache-dir .
conda deactivate
```
3.  Install the built `.whl` packages, into Blender's bundled python. The path to your 

Navigate to your Blender's python folder.
```bash
cd /Applications/Blender.app/Contents/Resources/3.4/python/bin/
```
Install the cached `.whl` into the bundled python that came with Blender.
```bash
./python3.10 -m pip install MDAnalysis --cache-dir ~/MDAnalysis-wheel
```

The <kbd>Install Packages</kbd> button should now successfully install the remaining packages.


:::

![](https://i.imgur.com/ePIhaGq.png)

The 'Install Packages' button should install the required python packages. Blender will freeze from anywhere between 30 seconds to several minutes, depending on the speed of your computer and internet connection. Once Blender un-freezes the button should disappear and be replaced by the Molecular Nodes panel. If this occurs then everything should be ready to use, try it out by downloading a structure from the pdb!

If the button does not disappear or you receive some kind of error message, search through the [issues page](https://github.com/BradyAJohnston/MolecularNodes/issues) for a potential solution. If you can't find the solution there, please open a new issue on the GitHub page. Please don't just DM or email me directly. It's better to do problem solving out in the open, as others might have the same issue or someone other than me may already have a solution!

# Start Importing Structures!

Molecular nodes should be fully installed. See the [Getting Started](getting-started.md) page on how to start importing into Blender!
