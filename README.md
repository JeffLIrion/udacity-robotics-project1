## Summary of Tasks

1. Build a single floor wall structure using the **Building Editor** tool in Gazebo. Apply at least one feature, one color, and optionally one texture to your structure. Make sure there's enough space between the walls for a robot to navigate.
2. Model any object of your choice using the **Model Editor** tool in Gazebo. Your model links should be connected with joints.
3. Import your structure and two instances of your model inside an empty **Gazebo World**.
4. Import at least one model from the **Gazebo online library** and implement it in your existing Gazebo world.
5. Write a C++ **World Plugin** to interact with your world. Your code should display “Welcome to ’s World!” message as soon as you launch the Gazebo world file.
These tasks are just the basic requirements for you to pass the project! Feel free to have fun designing and importing multiple models.

## Submission Folder

Here are the files that you need to include in your project submission folder:

* **model** folder:
  - Any object or robot designed in the Model Editor tool of Gazebo
  - A single floor structure designed in the Building Editor tool of Gazebo
* **world** folder:
  - Gazebo world file that includes the models
* **script** folder:
  - Gazebo world plugin C++ script
* **CMakeLists.txt** file to link the C++ code to libraries

## Steps

```sh
mkdir build
mkdir model
mkdir script
mkdir world

echo -e "*\n!.gitignore" > build/.gitignore
touch CMakeLists.txt
touch script/hello.cpp

export GAZEBO_MODEL_PATH="$(pwd)/model"
export GAZEBO_PLUGIN_PATH="${GAZEBO_PLUGIN_PATH}:$(pwd)/build"
```

### Build the plugin

```sh
# After sourcing ROS stuff...

cd build
cmake ..
make
```

### Modify the world file

Copy this code

```
<plugin name="hello" filename="libhello.so"/>
```

and paste it under the following line in the world file:

```
<world name="default">
```

### Launch the world with the plugin

```sh
cd ../world
gazebo myworld
```
