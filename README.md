# Fleet Highway Simulator

## Overview
Fleet Highway Simulator is a Java-based multithreaded application that tracks the operational status, fuel level, and mileage of a fleet of vehicles (Airplane, Ship, and Truck). Built using Java Swing, the project serves as a practical demonstration of concurrency control, race conditions, and thread-safe GUI updates.

## Key Features
* **Real-Time Multithreading:** Each vehicle (Airplane, Ship, Truck) runs on its own independent thread, continuously updating its fuel level and distance traveled.
* **Interactive GUI:** An intuitive Java Swing dashboard utilizing `BorderLayout`, `GridLayout`, and `BoxLayout` to display real-time metrics. Users can Play, Pause, Refuel, and Fix the simulation on the fly.
* **Race Condition Demonstration:** The program intentionally tracks a global variable (`Total_distance_travelled_by_all`) without synchronization to demonstrate how concurrent thread access leads to data loss and incorrect calculations.
* **Concurrency Fix:** By pressing the "Fix" button, the program engages a `synchronized(Object)` block, ensuring atomic operations and instantly correcting the race condition so the total distance calculates perfectly.
* **Thread-Safe UI:** Implements `SwingUtilities.invokeLater(() -> {})` to safely push UI updates to the Event Dispatch Thread (EDT), preventing UI freezing, glitching, or breaking during heavy thread loads.

## Project Structure
* `AbstractVehicle/` & `ConcreteVehicle/`: Contains the abstract base class and specific vehicle implementations (Airplane, Ship, Truck).
* `GlobalVariables/`: Houses the shared global state and the synchronization lock object.
* `Main/`: Contains `MainFrame.java`, which constructs the Swing GUI and handles the main simulation loop.
* `MakeVehicles/`: A factory-style class for initializing vehicle objects.
* `ThreadsHandler/`: Manages the independent `Runnable` threads for each vehicle's logic and handles the synchronization fix.

## How to Compile and Run

*Note: Ensure you have the Java Development Kit (JDK) installed and configured in your system's PATH.*

### For Linux Users
1. Open your terminal and navigate to the project folder:
   ```bash
   cd path/to/Java_Assignment3

```

2. Run the following command to compile, execute, and automatically clean up `.class` files upon closing:
```bash
javac Main/*.java ThreadsHandler/*.java AbstractVehicle/*.java ConcreteVehicle/*.java GlobalVariables/*.java MakeVehicles/*.java && java Main.MainFrame; find . -name "*.class" -type f -delete

```


*(Note: The command has been adapted from the original `BirthPlace` package structure to match the provided source code directories).*

### For Windows Users

1. Open Command Prompt and navigate to the project folder:
```cmd
cd path\to\Java_Assignment3

```


2. Run the following command to compile all Java files and run the program:
```cmd
javac Main\*.java ThreadsHandler\*.java AbstractVehicle\*.java ConcreteVehicle\*.java GlobalVariables\*.java MakeVehicles\*.java && java Main.MainFrame & del /s /q *.class

```


*(Note: Adapted for the multi-package directory structure).*

## Concepts Demonstrated

* **Multithreading & Concurrency:** Creating and managing multiple `Thread` and `Runnable` objects.
* **Synchronization:** Using `synchronized` blocks and lock objects to prevent race conditions on volatile variables.
* **Swing Event Dispatch Thread (EDT):** Safe GUI manipulation from background worker threads.
* **Object-Oriented Programming:** Inheritance, Abstraction, and Encapsulation.

```

```
