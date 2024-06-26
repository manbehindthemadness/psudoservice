# PseudoService
*A simple threaded task launcher that emulates unix service-unit style behavior*.

## Introduction

PseudoService is a simple scheduled threading task manager for Python applications. It provides a convenient way to manage tasks in a threaded environment.

## Usage

To use PseudoService, follow these steps:

1. Import the `Launcher` class from the `pseudoservice` module.
2. Define your tasks as a dictionary where each key represents a task name and each value is a dictionary specifying the task details.
3. Initialize an instance of `Launcher` with your tasks.
4. Start the tasks using the `start_tasks()` method.

### Example Usage

```
from pseudoservice import Launcher
import mytask_1
import mytask_2
import mytask_3

# Define tasks
tasks = {
    'My first task': {  # A task that will restart if the thread is closed.
        'task': mytask_1,
        'restart': True
    },
    'My second task': {  # A task with arguments that will run once and then close.
        'task': mytask_2,
        'args': [var_1, var_2, var_3]
    },
    'My third task': {  # A task with arguments and keyword arguments that will restart if the thread is closed.
        'task': mytask_3,
        'args': [var_1, var_2],
        'kwargs': {'varname_1': var_1, 'varname_2': var_2},
        'restart': True
    },
}

# Initialize and start tasks
task_launcher = Launcher(tasks)
task_launcher.start_tasks()
```

## Launcher Class
```
Launcher(tasks: dict)
```

Initialize the Launcher class with a dictionary of tasks.

## Methods

start_tasks(): Launches the threaded tasks.

## Task Configuration

Each task is defined by a dictionary with the following keys:

- task: Required. Specifies the task to be executed.
- args: Optional. Arguments to be passed to the task function.
- kwargs: Optional. Keyword arguments to be passed to the task function.
- restart: Optional. Specifies whether the task should restart if the thread is closed.
- delay: Optional. Specifies the delay (in seconds) between successive executions of the task.
Notes

- Tasks are executed in separate threads.
- The Launcher class handles task scheduling and thread management.

### Initialization

PseudoService can be installed from pip.
```
pip install pseudoservice
```
## Credits

PseudoService was developed by Manbehindthemadness.