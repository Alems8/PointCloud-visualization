# PointCloud-Visualizer

Display, edit and save colored point cloud in the DataFrame format.
Image of a render.

## General info
### Basic Usage:
This application is meant to be used to visualize and intercat real time with large point clouds. In order for the app to work is defined a [DataFrame format](README.md#DataFrame) which must be created before using the app.<br>
To open a file you can navigate the File menu, click on the open tab and select the file you want to view. Otherwise you can also use the shorcut `ctrl+o`.
<br> To save a screenshot of the point cloud you are viewing with the selected settings you can navigate the File menu and click the Save tab. Otherwise you can use the shortcut `ctrl+s`.
<br> To quit the app you can navigate the File menu and press exit or use the shortcut `ctrl+e`.
### Features:
- Density: the percentage of points displayed. It is a value between 1 and 100
- Alpha: describe the transparency of the points displayed. It is a value between 0.00 and 1.00.
- Point Size: point size in pixels
- Classes: in this treewidget are shown all the classes described in the dataset, each one with a different color and the informations about the number of points displayed, at the moment, and the accuracy score of the class. Using the checkbox next to the class name is possibele to enable or disable the classes from the current view. 
<br>****Important: at least one class must always be displayed.****
image of the features 
### Installation and First configuration:
To start using this app you need to configure a anconda environment with `python 3.9.13`, `PyQt5` and the following packages:
```
 - numpy 1.22.3
 - vispy 0.11.0
 - pyqtwebengine 5.15.7
 - scikit-learn 1.0.2
 - pandas 
 - pillow 
 ```
 Due to the nature of this app and the use of vispy to visualize the point clouds you need to have a GPU that support `OpenGl > 2.0` .
 Once you have configured the conda environment with all the above packages, you need to create a pandas DataFrame and convert it to a pickle file in order to be read by the app.
 #### DataFrame:
 The DataFrame is built thinking that this app may be used after a phase of segmentation of the original point cloud so this is the reason why it is structured as follows:<br>
 X,Y,Z,ClassName1,...,ClassNameN,GT
 As you can see there are n+4 columns. The first tree contains, respectively, the x,y,z of the point, the last one the correct class of the point. In between this 4 columns there are n columns which represents the classes of the point cloud and which contains the results of a hypothetical prediction phase during the segmentation of the point cloud.
<br> If you still want to use this tool without having predictions you can still do it populating the rows as follows:
 row i: 1875.4523 15.2456 1.245 0 0 0 0 1 4 , assuming you have 5 classes in your point cloud and the class corresponding to this point is the class 5 (you start counting the classes from 0).
#### First configuration:
 After you have created a DataFram in this format you need to convert it to a pickle file using the built-in function `DataFrame.to_pickle(path)`.
 Once you have saved a file with this extension you can start using the tool.
 
<br> After you have downloaded it you will have three .py files. In order to run the app you have to execute the `GUI.py` file.
## Limitations:
 At the moment the app can work only with maximum ten classes and point clouds which don't contains more than 10M points, in order to mantain the title of real time app, because otherwise it will become much slower rendering the points and doing all the updates operations.

  
