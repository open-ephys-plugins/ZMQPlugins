# Open Ephys 0MQ plugins
This reposiory contains the following first party plugins developed by Open Ephys that make use of the [0MQ library](http://zeromq.org/):
- **NetworkEvents**: A plugin that allows controlling basic functions of the GUI, such as recording toggle, as well as sending custom events via network using 0MQ
- **EventBroadcaster**: A plugin that send all events via a nerwork socket using 0MQ

## Installation
### Installing the 0MQ library
For windows, the required files are already included for the plugin
We have detailed instructions on our wiki on how to install the 0MQ for [Linux](https://open-ephys.atlassian.net/wiki/spaces/OEW/pages/491546/Linux) and [macOS](https://open-ephys.atlassian.net/wiki/spaces/OEW/pages/491555/macOS).

### Building the plugins
Building the plugins requires [CMake](https://cmake.org/). Detailed instructions on how to build open ephys plugins with CMake can be found in [our wiki](https://open-ephys.atlassian.net/wiki/spaces/OEW/pages/1259110401/Plugin+CMake+Builds).
We highly recommend building all three projects simultaneously using the configuration provided in the top-level Build folder, instead of the individual plugins. Building the plugins individually will need manual tweaking for them to find the OpenEphysHDF5 common library.
 