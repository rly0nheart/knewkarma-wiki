# Installation
## CLI & Python Library
The CLI and/or the Python library of Knew Karma can be installed directly from [PyPI](https://pypi.org/project/knewkarma)
> This assumes you have at least Python 3.10 or later installed on your system.
```
pip install knewkarma
```

## Building a Docker Image
1. Clone the repository to your system
```
git clone https://github.com/bellingcat/knewkarma.git
``` 
2. Move to the cloned *knewkarma* directory
```
cd knewkarma
```

3. Build the image
```
docker build -t knewkarma .
```

## GUI
The GUI instance of Knew Karma is only available for Windows systems, and can be installed by doing the following:

1. Download the latest setup files from the [releases page](https://github.com/bellingcat/knewkarma/releases/latest).
2. Extract the zip file and find `KnewKarmaSetup.msi` and `setup.exe`.
3. Run the `setup.exe` file if you do not have the .NET Desktop Runtime installed, otherwise run the `KnewKarmaSetup.msi`.
4. Follow the on-screen instructions.

> This installs Knew Karma and creates desktop and app menu shortcuts.
