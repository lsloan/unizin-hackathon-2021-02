# unizin-hackathon-02-21

This repository contains the non-sensitive parts of a Jupyter Notebook I wrote
as part of my participation in Day 1 of the February 2021 Unizin Hackathon,
which focused on using data marts.

## Installation & Configuration

To install the dependencies for the project, it should be a simple `pip install -r requirements.txt`, provided you have a version of Python on your machine.

To configure the BigQuery service account, you simply put the JSON file in the root of the project.
You'll need to update the specified JSON file name in the notebook in the second code cell.

Since the data marts used at the hackathon were limited to that event,
you'll also need to update the queries accordingly.

## Using iPython notebooks

Here are a few notes on working with iPython notebooks.

### Using a virtual environment as a kernel

If you are using Jupyter locally on your machine,
you can manage the needed dependencies by creating a kernel based o a virtual environment.
To create a kernel, do the following:

1) Create a virtual environment, and activate it.
   ```
   virtualenv venv
   source venv/bin/activate  # For MacOS
   ```
2. Install the dependencies.
   ```
   pip install -r requirements.txt
   ```
3. Run the following command.
   ```
   python -m ipykernel install --user --name venv --display-name "dev-hacks"
   ```

Then, when you run jupyter locally (i.e. `jupyter notebook`),
you can either specify `dev-hacks` as the kernel when 
creating a new notebook or click `Kernel` -> `Change Kernel` -> `dev-hacks`
to change the kernel of an existing  notebook.

### Excluding output data

When including iPython notebooks (for use with Jupyter) in a Git repository,
care must be taken to not commit sensitive data.
iPython notebook files contain the output of executed cells.
Fortunately, Jupyter now has a command for stripping output fields.
If you plan to commit a notebook, please execute the following before doing so.

```
jupyter nbconvert --ClearOutputPreprocessor.enabled=True --inplace [path to your notebook]
```