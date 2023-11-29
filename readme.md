# CCGenTool
(Common Criteria document Generation Tool)
![untitled](https://github.com/chienchanhsu/CCTool/assets/107752934/e6a8464c-5cec-445b-bff1-889ddbd6f059)

Common Criteria documentation application for Security Target using a hybrid approach by combining a rule-based System and random-forest as the method and Python with PySide6 as the primary programming language with a user-friendly Graphical User Interface (GUI).

This will provide easy suggestion based on the manufacturer device and automatically generate suggested Evaluation Assurance Level (EAL) with the Security Functional Requirements (SFR) that conforms with Common Criteria Framework.

## Getting Started
- Get Python 3.9 (Recomended) https://www.python.org/downloads/release/python-3913/
- Or Another Python version >3.9.13 (Not Recomended, workaround needed)
- Visual Studio Code (Recomended) https://code.visualstudio.com/

## Starting/Compiling the program

### Python 3.9
- Make Sure you have installed python 3.9 version
- Create new enviorment by using the `> Create Enviorment`


  ![image](https://github.com/chienchanhsu/CCTool/assets/107752934/2add9cb8-53ea-40c3-8b45-8f20a4c7a5a0)

  
- Then Choose `Venv`


  ![image](https://github.com/chienchanhsu/CCTool/assets/107752934/aba96fd8-dab3-4e6e-bd91-aaf03d1104c2)

  
- Choose the `Python 3.9.13` as the Main Intreperter


  ![image](https://github.com/chienchanhsu/CCTool/assets/107752934/0fb17680-001f-40e7-9d4f-d8469741d14b)

  
- You can install the `requirements.txt` by using the Visual Studio Code installer, or you still can install it later using this command  `pip install -r requirements.txt`.


  ![image](https://github.com/chienchanhsu/CCTool/assets/107752934/f88b81f7-f380-47a8-9bcf-9c57ab81dd40)


- Wait a moment for installing its packages.

  ![image](https://github.com/chienchanhsu/CCTool/assets/107752934/2293da6d-78ed-4414-bb60-5c47f70615be)


- To start the program, run `dashboard.py` to start the GUI

### Newer Python Version >3.9
- Due the old library, the `frozendict` are removed after python 3.9, so there are work around involved to run this program and fix the error when running `automatic` mode in this program
- To Start fix the library, please follow this steps
1. Edit this first `(Pyton Path)\lib\site-packages\frozendict\__init__.py`
2. in the line where `class frozendict(collections.Mapping)` is used. In your case, it’s line 16.
3. add `abc` in the `class frozendict(collections.Mapping)` to became  `class frozendict(collections.abc.Mapping)`
![Media1](https://github.com/chienchanhsu/CCTool/assets/107752934/138ebe40-e1ba-4050-bfbd-55f1d5ecbbf6)

## Building the program
- Execute the `dashboard.specs` using `pyinstaller` command
```bash
pyinstaller dashboard.spec
```
- Then executable will be compiled, the `.exe` or `program` are located in the `dist` folder
- After that, copy the `resources` folder into `dist` before running the program
- Make sure the resources folder in the same as the executable `.exe` / `Linux Executable`
- Run the `CCToolBox Beta` file to start the GUI

## Common Bugs and Debugging

### Database Error
Due of inproper closing the program or corrupt state, sometimes the database `cc_db.sqlite` are cleared until `0kb`, and may causes `Database error / Not found / SFR Not Found`

To fix this problem, simply copy the `cc_db.sqlite` from the resources folder, then run the program again.

And make sure the `cc_db.sqlite` has around `300KB` in size


### Load and save state inconsistant
This can be solved by writing some text to refresh the state, or you can clear the preview in the `final` sidebar and then click `clear`

### Inconsistant font
This bug still work in progress, the pasted text from another word document source may have inconsistant font size, you need to change it manually in the word document first.
