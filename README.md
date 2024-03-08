# Cross-sectional-Method

This repository contains the step-by-step tutorial to perform the cross-sectional method (CSM), of which the detailed principles are described in a recent paper. The dwg and pdf files of the *Tyrannosaurus rex* (AMNH 5027) model constructed in this study are also stored here. It is allowed to be downloaded publicly for non-commercial use.

**Remark:** This tutorial is based on AutoCAD 2020, other CAD software that can create rectangular arrays and export data to Excel can also do the job. The *T. rex* model is used here as an example. It is worth noting that most of the AutoCAD commands described below have corresponding function icons in the software. Users can either click on the icons or type the commands directly. The aim of this tutorail is to ensure that novice users of CAD software can replicate the CSM. If you have questions about this tutorial, please contact the author：jackevanchaos@outlook.com

## Load 2D images
First we need to create a new .dwg file. The CSM requires one side view or dorsal view image and a series of cross-sectional profiles to perform calculation. If the images are bitmaps, we can load them using the **imageattach** command.
![image](https://github.com/Pliosaurus-kevani/Cross-sectional-Method/blob/main/Images%20used%20in%20tutorial/load%20bitmaps.jpg)

## Create the silhouettes
After the images are loaded, we need to draw along the profiles to create silhouettes. This can be achived using the **spline** command.
![image](https://github.com/Pliosaurus-kevani/Cross-sectional-Method/blob/main/Images%20used%20in%20tutorial/create%20silhouette%201.jpg)

Afterwards, we need to use the **line** command to create segments that represent identity segments (red; see the paper for definition) of cross-sections and to separate the silhouettes.
![image](https://github.com/Pliosaurus-kevani/Cross-sectional-Method/blob/main/Images%20used%20in%20tutorial/create%20silhouette%202.jpg)

## Partition each slab into subslabs
For the definitions of "slab" and "subslab", please see the paper. We have separated the side view silhouette into multiple slabs in the last step, and one slab (white) of the *T. rex* is used here as example to show how to partition each slab into subslabs.

Prior to slicing, we need to measure the length of the slab. This can be achieved using the **measuregeom** command.
![image](https://github.com/Pliosaurus-kevani/Cross-sectional-Method/blob/main/Images%20used%20in%20tutorial/Measure%201.jpg)
![image](https://github.com/Pliosaurus-kevani/Cross-sectional-Method/blob/main/Images%20used%20in%20tutorial/Measure%202.jpg)

We create a vertical segment (set to green for this tutorial) at the anterior end of the slab using **line**. Then we use the **arrayrect** command to create a rectangular array from the green segment. 
![image](https://github.com/Pliosaurus-kevani/Cross-sectional-Method/blob/main/Images%20used%20in%20tutorial/Partition%201.jpg)

A settings bar for array creation would appear at the top.
![image](https://github.com/Pliosaurus-kevani/Cross-sectional-Method/blob/main/Images%20used%20in%20tutorial/Partition%202.jpg)

If we want to slice this slab into *n* subslabs, then *n+1* segments are required. For example, we want to slice this slab into 10 subslabs, then we set 1 row, 11 columns. The total length of all the columns is set to 1308.1958 mm, which is the length of the slab we measured above. We also need to deactivate the **Associative** setting.
![image](https://github.com/Pliosaurus-kevani/Cross-sectional-Method/blob/main/Images%20used%20in%20tutorial/Partition%203.jpg)

Then we get a slab truncated by multiple segments. If we forgot to deactivate the **Associative** setting in the last step, we can use the **x** command to split the array. We need to cut off the excess lengths of the segments. Before that, we need to delete the two segments at two ends of the slab.
![image](https://github.com/Pliosaurus-kevani/Cross-sectional-Method/blob/main/Images%20used%20in%20tutorial/Partition%204.jpg)

Then we cut off the excess lengths of the segments using **trim**.
![image](https://github.com/Pliosaurus-kevani/Cross-sectional-Method/blob/main/Images%20used%20in%20tutorial/Partition%205.jpg)

So far, we have had a slab partitioned into 10 subslabs.
![image](https://github.com/Pliosaurus-kevani/Cross-sectional-Method/blob/main/Images%20used%20in%20tutorial/Partition%206.jpg)
## Export lengths of identity segments
Now we need to create a new .dwg file, and paste the current slab to that file. Then we export lengths of the identity segments to Excel. This can be achieved using the **dataextraction** command. After typing this command and hitting enter, a GUI will occur.
![image](https://github.com/Pliosaurus-kevani/Cross-sectional-Method/blob/main/Images%20used%20in%20tutorial/dataextraction%201.jpg)

**Step 1:** At the request of AutoCAD, we select a folder to create a .dxe file (for example, dataextraction.dxe).
![image](https://github.com/Pliosaurus-kevani/Cross-sectional-Method/blob/main/Images%20used%20in%20tutorial/dataextraction%202.jpg)

**Step 2:** We don't need to change anything in this page. Click on "next".
![image](https://github.com/Pliosaurus-kevani/Cross-sectional-Method/blob/main/Images%20used%20in%20tutorial/dataextraction%203.jpg)

**Step 3:** We want to extract lengths of segements, so select "line".
![image](https://github.com/Pliosaurus-kevani/Cross-sectional-Method/blob/main/Images%20used%20in%20tutorial/dataextraction%204.jpg)

**Step 4:** There are many options here, but we only need two sets: "Length" and "Start X" in the "Geometry" category. "Start X" is the horizontal coordinate of the start of the line segment, which we will use for ordering。
![image](https://github.com/Pliosaurus-kevani/Cross-sectional-Method/blob/main/Images%20used%20in%20tutorial/dataextraction%205.jpg)

**Step 5:** We now need to click on the "Start X" icon to sort the data in ascending order.
![image](https://github.com/Pliosaurus-kevani/Cross-sectional-Method/blob/main/Images%20used%20in%20tutorial/dataextraction%206.jpg)

**Step 6:** Then AutoCAD will export the data in a .xls file to the folder we selected in Step 1.
![image](https://github.com/Pliosaurus-kevani/Cross-sectional-Method/blob/main/Images%20used%20in%20tutorial/dataextraction%207.jpg)
![image](https://github.com/Pliosaurus-kevani/Cross-sectional-Method/blob/main/Images%20used%20in%20tutorial/dataextraction%208.jpg)

### We have created a template .dxe file. If we want to extract the identity segments of other slabs, we do not need to replicate the 6 steps above. Instead, we can select "use previous extraction as a template", and replace the original .dxe file. All we need do now is to click on "next" until the data are exported. Note that an error would be returned if the user tries to replace the original .xls file while it is opened in Excel!  
![image](https://github.com/Pliosaurus-kevani/Cross-sectional-Method/blob/main/Images%20used%20in%20tutorial/dataextraction%209.jpg)

## Calculate $\varphi$ and $\psi$ for each cross-section
The **measuregeom** command can also measure the area and circumference of a 2D object. For example, here is a cross-section of the *T. rex* model (identity segment marked in red). We can select the "area-object" option in **measuregeom** and click on the yellow outline, then AutoCAD will return the area and circumference at the bottom.
![image](https://github.com/Pliosaurus-kevani/Cross-sectional-Method/blob/main/Images%20used%20in%20tutorial/phi%201.jpg)
![image](https://github.com/Pliosaurus-kevani/Cross-sectional-Method/blob/main/Images%20used%20in%20tutorial/phi%202.jpg)

Then the $\varphi$ can be calculated using $\varphi=\dfrac{S}{d^2}$, where $d$ is the length of the identity segment. The $\psi$ value can be obtained in a similar way.

### So far, we have obtained all the data we need to perform calculation, which can be easily down in Excel.
