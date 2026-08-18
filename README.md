# Designing a Multistable Structure Optimized for Robotic Applications

Final Mechanical Engineering Project
Faculty of Mechanical Engineering, Technion – Israel Institute of Technology

**Author:** Carly Rachelson
**Supervisor:** Dr. Lior Salem
**Academic year:** 2025–2026

## Project Overview

This repository contains the CAD models, MATLAB calculations, printable files, and fabrication files developed during the project **Designing a Multistable Structure Optimized for Robotic Applications**.

The project investigated custom multistable structures for soft robotic applications, with particular focus on reconfigurable conical frusta (RCF). The main stages of the project were:

1. Determining suitable geometric relationships for bistability and improved multistable behaviour.
2. Investigating geometric additions to improve the mechanical behaviour of the RCF structure.
3. Exploring alternative fabrication methods and methods for introducing prestress.
4. Considering alternative multistable structural concepts for future development.

The principal fabrication method investigated was 3D printing using TPU.

---

## Repository Structure

### `CAD_files/`

Contains the SolidWorks models and exported printable geometry generated throughout the project.

#### `1. Finding_Ratios/`

CAD models used during the main iterative investigation of RCF geometry.

The parameters investigated included:

* active and passive frustum thickness
* frustum heights
* frustum angles
* radius
* relative active/passive geometry
* stacked-element behaviour

The parameters were found to be strongly coupled and should therefore not be optimized independently.

##### `Final_Iteration_final_ratio/`

Contains the best-performing geometry obtained from the ratio investigation.

Important files:

* `Final_Ratio_Iteration.SLDPRT` — editable SolidWorks model
* `Final_Ratio_Iteration.STL` — printable geometry
* `Final_Ratio_Iteration_print_settings.gcode.3mf` — associated printing setup

This geometry was used as the starting point for the subsequent RCF-addition investigation.

##### `Iterations/`

Contains representative CAD models from the iterative parameter investigation.

These files document changes to parameters including:

* frustum angle
* frustum height
* passive-element thickness
* active/passive geometry
* hinge and compliant-region concepts

These models are retained primarily to document the design process and provide starting points for future parameter studies.

##### `Stacked_Attempts/`

Contains early attempts to connect multiple RCF elements.

* `RCF_stacked_attempt_1.SLDASM`

Stacking introduced additional mechanical interactions between neighbouring elements and was therefore treated separately from the behaviour of a single RCF unit.

---

#### `2. Variation(b)/`

Contains models investigating the alternative orientation of the RCF geometry.

Files include:

* `Variation_b_Mathematical_model_values.SLDPRT`
* `Variation_b_initial_test.SLDPRT`

This variation was investigated because the available analytical model used an RCF orientation different from the principal geometry adopted during the project.

---

#### `3. Design_concepts/`

Contains preliminary alternative multistable design concepts that do not rely directly on the final RCF architecture.

Examples include:

* kirigami-inspired geometry
* cut/origami-inspired geometry

These concepts were not developed to the same level as the RCF design but are retained as possible starting points for future work.

---

#### `4. RCF_Additions/`

Contains the second major stage of RCF development, in which additional geometric features were introduced after establishing the best-performing basic RCF geometry.

##### `Additions_variations/`

Contains investigated modifications including:

* relief slots
* slits
* collar-dimension changes
* neck/collar additions
* passive-element stiffening

The most important conclusion from these iterations was that increasing stiffness did not necessarily improve multistability. The passive component must still participate in the deformation of the complete structure.

The collar/neck modification was beneficial because it reduced undesirable deformation at the transition between the active and passive regions.

Slits and excessive passive-element stiffening were not retained in the final design.

##### `Final_Iteration/`

Contains the final geometry obtained after investigating the RCF additions.

Important files:

* `Final_iteration_additions.SLDPRT`
* `Final_iteration_additions.STL`

For future continuation of the RCF design, this folder and `1. Finding_Ratios/Final_Iteration_final_ratio/` are the recommended starting points.

---

#### `5. Overcurvature/`

Contains models used to investigate the introduction of prestress through overcurvature.

Instead of printing the RCF as a completely closed axisymmetric structure, an angular section was removed so that closing the structure introduced a geometric mismatch and internal prestress.

Files include examples corresponding to different imposed overcurvature values, as well as a preliminary gluing/clamping concept.

The overcurvature method demonstrated a possible route for introducing prestress; however, manual alignment and bonding were difficult to perform repeatably.

Related calculations are contained in:

`Matlab_files/Overcurvature_parameter_calculator.mlx`

---

#### `6. Silicone_Molds/`

Contains the mold components developed for an alternative silicone fabrication method.

The mold was separated into multiple components to allow removal of the cured RCF geometry.

Files include:

* `Mold_part1.SLDPRT`
* `Mold_part2_.SLDPRT`
* `Mold_part3.SLDPRT`
* `bottom_mold.gcode.3mf`

Silicone molding allowed thinner walls to be investigated than were practical using the selected TPU printing process. However, the resulting silicone structures did not provide sufficient rigidity for the intended robotic application.

---

## `Matlab_files/`

Contains MATLAB Live Scripts used during the project.

### `Mathematical_Model_parameters_color_plots.mlx`

Implements the available analytical RCF/Pop Toob model and was used to investigate the influence of geometric parameters and generate the parameter maps presented in the project report.

The model was used primarily to identify initial geometric regions for investigation. Final design selection was based on experimental iteration because the analytical formulation did not fully represent the material and fabrication behaviour of the printed TPU structures.

### `Overcurvature_parameter_calculator.mlx`

Calculates the geometry required to generate selected levels of overcurvature and prestress in the open RCF specimens.

---

## `g.code_files/`

Contains saved 3D-printing project files and associated print settings.

### `Final_Ratio_Iteration_print_settings.gcode.3mf`

Printing setup associated with the best-performing RCF geometry obtained during the ratio investigation.

### `TPU_PLA_multimaterial_rigidity.gcode.3mf`

Printing setup from the PLA–TPU multi-material investigation.

The multi-material investigation used TPU for the deformable region and PLA for the stiffer region. Although the method successfully produced regions with substantially different stiffnesses, increasing the rigidity of the passive component did not automatically improve multistability.

---

## Recommended Starting Points

For someone continuing this research, the following files are recommended as the most useful starting points:

**Best geometry from the ratio investigation**

`CAD_files/1. Finding_Ratios/Final_Iteration_final_ratio/Final_Ratio_Iteration.SLDPRT`

**Final geometry incorporating successful RCF additions**

`CAD_files/4. RCF_Additions/Final_Iteration/Final_iteration_additions.SLDPRT`

**Printable final geometry**

`CAD_files/4. RCF_Additions/Final_Iteration/Final_iteration_additions.STL`

**Analytical model**

`Matlab_files/Mathematical_Model_parameters_color_plots.mlx`

**Overcurvature calculations**

`Matlab_files/Overcurvature_parameter_calculator.mlx`

---

## Main Design Findings

The following conclusions are particularly important when continuing development:

* The RCF geometric parameters are strongly coupled and should not be optimized independently.
* The most successful configurations generally satisfied:

  * α₁ < α₂
  * h₁ > h₂
  * t₁ < t₂
* Exaggerating these differences does not necessarily improve stability.
* A collar/neck at the active–passive transition improved deformation control and repeatability.
* Excessive passive-element stiffening reduced the desired multistable behaviour.
* Slits increased local compliance but did not improve the required snap-through behaviour.
* Stacking introduces interactions between neighbouring RCF units and must be considered separately from the response of an isolated element.
* Silicone molding enabled thinner structures but provided insufficient rigidity.
* PLA–TPU multi-material printing successfully generated regions of different stiffness but did not provide the expected improvement in multistability.
* Overcurvature is a promising method for introducing prestress, although a more repeatable assembly or fabrication method is required.

---

## File Types

The repository contains several file formats:

* `.SLDPRT` — SolidWorks part files
* `.SLDASM` — SolidWorks assembly files
* `.STL` — exported printable geometry
* `.3mf` — 3D-printing project and slicing files
* `.mlx` — MATLAB Live Scripts

SolidWorks files should preferably be opened using a compatible version of SolidWorks. STL files are provided where available to allow fabrication without requiring the original CAD software.

---

## Project Report

The complete design process, theoretical background, experimental observations, fabrication methods, limitations, and recommendations are documented in the associated final project report:

**Designing a Multistable Structure Optimized for Robotic Applications**

The report should be consulted together with this repository, as many of the CAD files represent intermediate experimental iterations whose mechanical behaviour and purpose are described in greater detail there.
