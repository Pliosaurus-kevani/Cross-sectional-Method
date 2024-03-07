# Cross-sectional-Method

This repository contains the step-by-step tutorial to perform the cross-sectional method (CSM), of which the detailed principles are described in a recent paper. The dwg and pdf files of the *Tyrannosaurus rex* (AMNH 5027) model constructed in this study are also stored here. It is allowed to be downloaded publicly for non-commercial use.

**Remark:** This tutorial is based on AutoCAD 2020, other CAD software that can create rectangular arrays and export data to Excel can also do the job. The *T. rex* model is used here as an example. It is worth noting that most of the AutoCAD commands described below have corresponding function icons in the software. Users can either click on the icons or type the commands directly. The aim of this tutorail is to ensure that novice users of CAD software can replicate the CSM. If you have questions about this tutorial, please contact the author：jackevanchaos@outlook.com

## Load 2D images
First we need to create a new .dwg file. The CSM requires one side view or dorsal view image and a series of cross-sectional profiles to perform calculation. If the images are bitmaps, we can load them using the **imageattach** command.

## Create the silhouettes
After the images are loaded, we need to draw along the profiles to create silhouettes. This can be achived using the **spline** command. Afterwards, we need to use the **line** command to create segments that represent identity segments (see the paper for definition) of cross-sections and to separate the silhouettes.

## Partition each slab into subslabs
For the definitions of "slab" and "subslab", please see the paper. We have separated the side view silhouette into multiple slabs in the last step, and one slab of the *T. rex* is used here as example to show how to partition each slab into subslabs.

Prior to slicing, we need to measure the length of the slab. This can be achieved using the **measuregeom** command.

We create a vertical segment (set to green for this tutorial) at the anterior end of the slab using **line**. Then we use the **arrayrect** command to create a rectangular array from the green segment. 

A settings bar for array creation would appear at the top.

If we want to slice this slab into *n* subslabs, then *n+1* segments are required. For example, we want to slice this slab into 10 subslabs, then we set 1 row, 11 columns. The total length of all the columns is set to 1308.1958 mm, which is the length of the slab we measured above. We also need to deactivate the **Associative** setting.

Then we get a slab truncated by multiple segments.

If we forgot to deactivate the **Associative** setting in the last step, we can use the **x** command to split the array. We need to cut off the excess lengths of the segments. Before that, we need to delete the two segments at two ends of the slab.

Then we cut off the excess lengths of the segments using **trim**.

So far, we have had a slab partitioned into 10 subslabs.

## Export lengths of identity segments
Now we need to create a new .dwg file, and paste the current slab to that file. Then we export lengths of the identity segments to Excel. This can be achieved using the **dataextraction** command. After typing this command and hitting enter， a GUI will occur.
