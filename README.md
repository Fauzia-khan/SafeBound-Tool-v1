# SafeBound-Tool-v1


SafeBound is a modular end-to-end pipeline for scenario-based safety testing of Automated Driving Systems (ADS). It streamlines the entire workflow, from scenario selection and implementation to configuration, simulation, data collection, safety evaluation, and the generation of visualization and simulation summary reports.



---

\## GUI for the Scenario Selection Module



<p align="center">

&nbsp; <img src="SafeBound\_v1/images/Main\_WIndow.png" alt="Main Window" width="600">  

</p>



\## Workflow 

&nbsp;\*\*Launch the Tool\*\* – Run the main Python script.

&nbsp;

\*\*1. Scenario Selection Module:\*\* – Prioritizes and selects the test scenario based on the SSTSS process. It takes four inputs:



i. \*\*Select Catalog\*\* – Choose the dataset region (US, Singapore, Other). 

&nbsp;        

ii. \*\*Select ODD\*\* – Narrow down scenarios based on operational design domain, i.e., (Dynamic, Environmental, Scenery ).



iii. \*\*Select Dataset\*\* – Choose the dataset US, Europe, or Singapore.



iv. \*\*Select Simulator\*\* – Choose the simulator.(Currently, you can select CARLA)



\_Output.\_ --> Final list of Test Scenarios.xlsx



\*\*2. \*\* Scenario Implementation Module:\*\* Maps the top-prioritized scenario into a Python script that defines the actors and their corresponding behaviors. <br>

\_Output\_ --> (<scenarioname.py>)



\*\*3. Scenario Configuration Module:\*\* Configures the simulation environment and applies the selected input parameters in <scenario\_name.py>. <br>

\_Output\_ --> (<scenarioname.xml>) 



\*\*4. \*\* Simulator and ADS Integration Module:\*\* Sets up the simulation environment, including CARLA, Scenario Runner, and Autoware Mini. <br>

\_Output\_ --> (simulation setup is ready)



\*\*5. Scenario Execution Module:\*\* Runs the configured scenario in CARLA using the integrated simulation setup. <br>

\_Output\_ --> (<scenarioname.log>)  and \_Output\_ --> (<scenarioname.json>)



\*\*6. \*\* Data Collection Module:\*\* Captures all relevant simulation outputs, including timestamps, positions, and speeds of all actors involved.<br>

\_Output\_ --> (<scenarioname\_data.csv>)



\*\*7. \*\* Safety Metrics Evaluation Module:\*\* Calculates the safety metrics for evaluating ADS performance.  <br>

\_Output\_ --> (<scenarioname\_metrices.py>)



\*\*8. Data Visualization and Report Module:\*\* Generates plots and summary reports based on the collected data.<br>

\_Output\_ --> (<scenario\_name\_metrice.png>)  and \_Output\_ --> (<scenarioname\_summary.txt>)





\## Requirements

The SafeBound Tool requires a Linux-based environment with ROS and a supported simulator. The recommended Supported Operating System is Ubuntu 20.04 LTS (recommended).

Windows is not supported because key components (Autoware\_mini) do not run natively on Windows.





\## Installation

\### 1. Install and Configure CARLA (for Simulation Execution)



Download CARLA 0.9.13

https://carla.org/



Extract CARLA to your preferred location

Add CARLA PythonAPI to PYTHONPATH:

```bash

export PYTHONPATH=$PYTHONPATH:/path/to/CARLA\_0.9.13/PythonAPI/carla/dist/carla-0.9.13-py3.8-linux-x86\_64.egg

export PYTHONPATH=$PYTHONPATH:/path/to/CARLA\_0.9.13/PythonAPI/carla



```

(Replace paths with your system locations.)

\### 2. Autoware\_mini Installation 

Clone the repository into your ROS workspace:

```bash

cd ~/catkin\_ws/src

git clone https://github.com/UT-ADL/autoware\_mini.git

```

Install dependencies:

```bash

rosdep install --from-paths . --ignore-src -r -y

```

Build:

```bash

bash

cd ~/catkin\_ws

catkin\_make

```

Source the workspace:

```bash

bash

source ~/catkin\_ws/devel/setup.bash

```

For complete instructions, refer to:

https://github.com/UT-ADL/autoware\_mini



\### 3. ScenarioRunner Installation



Download ScenarioRunner (compatible with CARLA 0.9.13):

```bash

git clone https://github.com/carla-simulator/scenario\_runner.git



```

Set the root path inside config.py:

```bash

SCENARIO\_RUNNER\_ROOT = "/home/user/scenario\_runner"



```

5\. Configure SafeBound Tool Paths



Edit config.py inside the tool:

```bash

TOOL\_ROOT = "/path/to/SafeBound"

CARLA\_ROOT = "/path/to/CARLA\_0.9.13"

SCENARIO\_RUNNER\_ROOT = "/path/to/scenario\_runner"

RESULTS\_DIR = "os.path.join(TOOL\_ROOT, "Data\_Collection\_Module", "raw\_data"



```







\### 4. SafeBound-Tool Installation

\### 1. Clone the Repository

```bash



\# 1. Clone the repository

git clone https://github.com/<your-username>/SafeBound-Tool.git



\# 2. Navigate into the project directory

cd SafeBound-Tool/SafeBound\_Modules



\# 3. Create a Python virtual environment (first time only)

python -m venv venv



\# 4. Activate the virtual environment

\# Linux

source venv/bin/activate



\# 5. Install Python dependencies (Python 3.8+ recommended)

pip install -r requirements.txt



\# 6. Run the main tool

python main.py

```





\## Demo Video

\[Click here to watch the tool demo video](https://drive.google.com/file/d/1XPXzFDNAYXQR10g7PQslKZQKBmrmNhln/view?usp=sharing)



\## Authors

Fauzia Khan, Ali Ihsan GÜllÜ, Hina Anwar, Deitmar Pfahl, "SafeBound: A Modular Tool Chain for End-to-End Safety Evaluation of Automated Driving Systems".



---

DS.



