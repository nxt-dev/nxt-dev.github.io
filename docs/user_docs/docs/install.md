<h1>Standalone Installation</h1>

## Linux, Mac, Windows

*If you're trying to install on Windows in a Python 2 environment see [here](#windows-python-27)*

To install the latest release directly from [PyPi](https://pypi.org/project/nxt-editor/) follow the following steps.

!!! Note
    The `nxt-core` is *just* the Python backend of NXT, it does not include the visual editor.  
    The core will automatically install with the `nxt-editor`.

#### Video

<iframe width="400" height="270" src="https://www.youtube.com/embed/yaSjF_IKMRY" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
<iframe width="400" height="270" src="https://www.youtube.com/embed/gyaR7YgfulE" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

#### Written

- First time install
    - For just the cli and backend: `pip install nxt-core`
    - For the backend and the visual editor: `pip install nxt-editor`
- Launch (nxt editor)
    - `nxt ui`
- Update
    - `pip install -U nxt-core`
    - `pip install -U nxt-editor`

To execute a graph with the nxt Python core, use the following:
```python
import nxt
nxt.execute_graph('path/to/graph.nxt')
``` 

<br>

---

## Windows (Python 2.7)
*If you're installing into a Python 3.7.x environment you can use the above [steps](#linux-mac-windows)*

!!! Note
    These steps are *only* necessary if you want to use the nxt **standalone editor** outside of Maya.  
    The `nxt-core` will pip install on Windows Python 2.7 without issue.

Due to the limited availability of PySide2 on Windows for Python 2.7 the steps to install on Windows are slightly more involved.
For the simplest instructions, please follow the [developer installation steps](#developer-installation).  
If you're comfortable working in an IDE and using git we suggest you follow 
the [contributing documentation](https://github.com/nxt-dev/nxt_editor/blob/release/CONTRIBUTING.md).

<br>

---

## Maya plugin
Our Maya plugin comes with both a visual editor and the core. We've tested Maya 2018-20 on all platforms.

#### Video

<iframe width="560" height="315" src="https://www.youtube.com/embed/VoEz0oyTwzU" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

#### Written

- Install:
    1. Download the maya module(`nxt_maya.zip`) from the [latest release](https://github.com/nxt-dev/nxt_editor/releases/latest)
    2. Follow the `nxt_maya` <a href="https://github.com/nxt-dev/nxt_editor/blob/release/integration/maya/README.md" target="_blank">README</a> instructions (also included in the download)
- Launch:
    1. Load `nxt_maya` plugin in Maya
    2. Select the `nxt` menu from the menus at the top of Maya
    3. Click `Open Editor`
- Update:
    1. Download the `nxt_maya` zip from the [latest release](https://github.com/nxt-dev/nxt_editor/releases/latest)
    2. Extract the zip and replace the existing `nxt_maya` files with the newly extracted files.
    3. Re-launch Maya

#### Planned plugins:
- Houdini 
- Nuke

<br>

---

# Developer Installation
See our [contributing documentation](https://github.com/nxt-dev/nxt_editor/blob/release/CONTRIBUTING.md)


#### NXT Python Dev Environment (Miniconda)
The following steps are only needed if you intend on contributing to the NXT codebase or you are trying to install NXT standalone on Windows Python 2.7.
To get the correct Python environment setup on your Windows machine you will 
need to follow these steps. 
The nxt environment is specified in our `nxt_env.yml`.
 
- Conda is best installed via [miniconda](https://docs.conda.io/en/latest/miniconda.html). 
We recommend **not** adding conda python to your system path and **not** making it your system python.
- You can either clone the nxt source from our [core repo](https://github.com/nxt-dev/nxt) / [editor repo](https://github.com/nxt-dev/nxt_editor) or download the desired
 [core release](https://github.com/nxt-dev/nxt/releases) / [editor release](https://github.com/nxt-dev/nxt_editor/releases) source code zip and extract it.
- Lets assume you place the source code at `C:/Projects/nxt`
- Launch the **Anaconda Prompt** and install dependencies:
    `conda env create -f C:/Projects/nxt/nxt_env.yml`
#### Launching the nxt editor
- From Anaconda Prompt
    - `conda activate nxt`
    - `cd C:/Projects/nxt`
    - `python -m nxt.cli ui`

<br>

#### Bootstrapping nxt

Tested with Maya2018/19/20, Houdini18, Nuke11,12

!!! warning
    This setup is temporary, and will eventually be replaced with a command
     port connections with host plugins. There is also lack of support in
      apps like photoshop, UE4 (qt library issues).

Find your conda env with this command in the Anaconda Prompt: `conda info --envs` 
Copy the following code into Maya and edit  `NXT_PATH` and `ENV_PATH` to reflect your environment. You can then drag it to your shelf or save it to a file, up to you.

    import sys
    import os
    # path to your nxt clone
    NXT_PATH = '~/Projects/Sun/nxt'
    # path to conda env
    ENV_PATH = 'C:/ProgramData/Miniconda2/envs/nxt/Lib/site-packages'
    # Default file to open, can be None
    LAUNCH_FILE = '~/Projects/SomeGraph.nxt'
    if ENV_PATH not in sys.path:
        sys.path.append(os.path.expanduser(ENV_PATH))
    if NXT_PATH not in sys.path:
        sys.path.append(os.path.expanduser(NXT_PATH))
    from Qt import QtCore
    import nxt_editor.main_window
    instance = nxt_editor.main_window.MainWindow(filepath=LAUNCH_FILE)
    if sys.platform == 'win32':
        instance.setWindowFlags(QtCore.Qt.Window)
    instance.show()
    # To force close the instance run this line:
    # instance.close()

##### Optional window attach

To attach to the main window in Nuke

    def _nuke_main_window():
        """Returns Nuke's main window"""
        for obj in QtWidgets.QApplication.topLevelWidgets():
            if (obj.inherits('QMainWindow') and
                    obj.metaObject().className() == 'Foundry::UI::DockMainWindow'):
                return obj
        else:
            raise RuntimeError('Could not find DockMainWindow instance')
    nuke_window = _nuke_main_window()
    instance = nxt_editor.main_window.MainWindow(parent=nuke_window, filepath=LAUNCH_FILE)

To Attach to the main window in Houdini

    from hutil.Qt import QtCore
    instance = nxt_editor.main_window.MainWindow()
    instance.setParent(hou.qt.mainWindow(), QtCore.Qt.Window)

To Attach to the main window in Maya

    import maya.OpenMayaUI as mui
    pointer = mui.MQtUtil.mainWindow()
    maya_window = QtCompat.wrapInstance(long(pointer), QtWidgets.QWidget)
    instance = nxt_editor.main_window.MainWindow(parent=maya_window)
