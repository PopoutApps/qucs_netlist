# qucs-netlist

Converts Qucs schematic files into a form suitable for a PCB design application. It uses a Qucs schematic file to add components to a netlist file. If there is also a Qucs .sim file with the same name but the .sim extension, it will use that to create the nets, if not it will attempt to run Qucs to create a .sim file, if Qucs has been installed that should succeed, but it won't work from qucs-s. If no .sim file was present and can't be created, the output netlist file will contain components but no nets.

INSTALLATION
Assuming your system already has Python3 and PIP installed, type:
  pip install qucs-netlist==0.0.5

RUNNING
To process a schematic file in your current directory, type:
	python3 -m PopoutApps.qucs-netlist mycircuit.sch

The output file will be called mycircuit.net

If you run it again it will not overwrite the existing file, unless you add a 'y' at the end of the line:
	python3 -m popoutApps.qucs-netlist mycircuit.sch

ERRORS
The program will print a warning line for each component which is not yet in the reference data file: 
	Warning: Unknown component type not converted: D2 Diac

The program may call a qucs process which produces many lines (100+) of errors in the terminal. They are mostly to do with missing fonts and don't affect the output file. Ignore these.

SCOPE
There is a maximum 100 components.
The exported file can be imported by DIY Layout Creator (available from their website or from Flathub) and VeroRoute, but it could be imported into any application provided it accepted the component types in the reference data file. Alternatively another .dat file could be provided with component names acceptable to the application.
