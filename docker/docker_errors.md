# Gazebo model error ( Can not load gazebo without internet)
## gazebo keep requesting gazebo models to server even if internet is not connected
- download menifest gazebo model to .gazebo folder as 'models'
```
cd ~/.gazebo
git clone https://github.com/osrf/gazebo_models.git models
```
- edit GAZEBO_MODEL_DATABASE_URI as null
```
nano /usr/share/gazebo/setup.sh
nano /usr/share/gazebo-<version>/setup.sh
```
```
export GAZEBO_MASTER_URI=http://localhost:11345
export GAZEBO_MODEL_DATABASE_URI=
export GAZEBO_RESOURCE_PATH=/usr/share/gazebo-9:${GAZEBO_RESOURCE_PATH}
export GAZEBO_PLUGIN_PATH=/usr/lib/x86_64-linux-gnu/gazebo-9/plugins:${GAZEBO_PLUGIN_PATH}
export GAZEBO_MODEL_PATH=/usr/share/gazebo-9/models:${GAZEBO_MODEL_PATH}
export LD_LIBRARY_PATH=${LD_LIBRARY_PATH}:/usr/lib/x86_64-linux-gnu/gazebo-9/plugins
export OGRE_RESOURCE_PATH=/usr/lib/x86_64-linux-gnu/OGRE-1.9.
```
- after edit, source
```
source /usr/share/gazebo/setup.sh
source /usr/share/gazebo-<version>/setup.sh
```
- copy config to model.config in gazebo folder
```
cp ~/.gazebo/models/.git/config ~/.gazebo/models/.git/model.config
```
- and run command
```
gazebo --verbose
```
