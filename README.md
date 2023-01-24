# Cadmium UDP

This project is a fork from [this repo](https://github.com/jwehorner/Cadmium_UDP) with some minor changes to make it run in real time under Windows.

# Run

To build the model and run the test drivers follow these steps:
* Open Visual Studio, then go to `File -> Open -> Folder` and choose the root folder `Cadmium_UDP`. 
* Then the CMake should automaticaly run. Otherwise, go to `Project -> Configure Cache`. Make sure that the CMake configuration `Test` is chosen.

After this point a folder build should have been created in the root folder. Inside, it should be a folder `_deps` with the `cadmium`, `destimes` and `rt-cadmium`.

* Finally, go to `Build -> Build All`.

You will find the executables under `build`.

# Check Real Time

You should check that the models run in real time through PowerSHell with the help of `Measure-Command{}`. To check this run:
```
PS C:\Users\Usuario\Documents\repositories\Cadmium_UDP\build> Measure-Command {.\td_udp_input.exe}
```
