# XYZ File Extraction and Visualization

This README provides instructions on how to extract compressed .xyz files and visualize them using Python libraries MDAnalysis and nglview.

## File Extraction

The .xyz files are compressed and split into multiple .tar.gz files. Use the following bash commands to extract them:

```bash
# For files split into multiple parts (e.g., R19P.xyz and T30P.xyz):
cat R19P.tar.gz.* | tar xzf -
cat T30P.tar.gz.* | tar xzf -

# For files in a single part (e.g., C30P.xyz and O30P.xyz):
tar xzf C30P.tar.gz.00
tar xzf O30P.tar.gz.00
```

After extraction, you should have the following .xyz files:
- C30P.xyz
- O30P.xyz
- R19P.xyz
- T30P.xyz

## Visualization

To visualize the extracted .xyz files, you can use Python with MDAnalysis and nglview libraries. Here's a Python script to visualize any of the extracted .xyz files:

```python
import MDAnalysis as mda
import nglview as nv

# Replace 'filename.xyz' with the name of the .xyz file you want to visualize
filename = 'filename.xyz'

# Create a universe object from the .xyz file
universe = mda.Universe(filename)

# Create a view of the universe
view = nv.show_mdanalysis(universe)

# Add a ball and stick representation
view.add_representation('ball+stick')

# Center the view
view.center()

# Display the view
view
```

To use this script:
1. Make sure you have MDAnalysis and nglview installed. You can install them using pip:
   ```
   pip install MDAnalysis nglview
   ```
2. Replace 'filename.xyz' with the name of the .xyz file you want to visualize (e.g., 'R19P.xyz').
3. Run the script in a Jupyter notebook or in an environment that supports nglview visualization.

This will create an interactive 3D visualization of the molecular structure in the .xyz file.
```
