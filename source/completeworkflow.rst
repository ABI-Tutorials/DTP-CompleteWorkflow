=================
Complete Workflow
=================

This module covers the complete workflow from the acqusition of medical images through to a clinical outcome or clinical tool.  

Overview
======== 

At this point we have covered the individual stages that take us from some clinical observation or clinical experiment through to creating clinical outcomes.  We shall now turn to looking at a complete workflow, that is starting from some clinical data and finishing with a prediction for clinical use.

In this module we will use the musculoskeletal system to illustrate the complete workflow.  Firstly we will consider the partial case of a complete workflow where we will analyse a horses fetlock joint to gain understanding on wear and abrasion and how this relates to injury.  Then we will look at a much more complete workflow, the femur morphometric workflow, which starts from a set of patient specific anatomical feducial markers and ends with the femur measurements of a specific patient.  The measurements taken from the femur may then be used to provide assistance to a clincian on deciding on a course of action for a positive clinical outcome.

The Musculo-Skeletal System
===========================

The musculo-skeletal (MSK) system ... has a great deal importance in the clinical setting.  With so many people suffering from osteoathritis and other musculo-skeletal diseases the impact of reducing patient suffering is huge.  From a computational physiology aspect we are taking patient measurement and constructing a suitable model that can be used to predict behaviour, for example a wear pattern of a joint acheived through computing joint stress and strain.

MSK Introductory Workflow
=========================

Task one is to have a look at the horse fetlock joint analysis workflow.  In this workflow we will take a set of measurements that will be used to characterise the joint.  With this information we will predict the liklehood of injury and try to determine a training regime that minimises the risk of injury.

.. figure:: _images/task1workflow.png
   :name: dtp_cp_cwf_tsk1_wkfl
   :align: center
   :alt: Task 1 workflow image
   
   Task 1 workflow horse fetlock characterisation

In this workflow [shown in :numref:`dtp_cp_cwf_tsk1_wkfl`] there are six steps.  It starts with reading in a database of horse fetlock mesh coordinate frame definitions and the selection of a fetlock mesh.  The corresponding coordinate frame definition is read in for the mesh selected and passed to the 'Hoof Measurement' step along with the fetlock mesh itself.  The first three steps in this workflow are non-interactive steps, they are configured proir to executing the workflow.  The 'Hoof Measurement' step is an interactive step for making measurements along the sagittal ridge of the fetlock joint.  

.. figure:: _images/task1initial.png
   :name: dtp_cp_cwf_tsk1_ini
   :align: center
   :alt: Task 1 Initial view
   
   Initial view of the 'Hoof measurement' step

:numref:`dtp_cp_cwf_tsk1_ini` shows the initial view of the 'Hoof Measurement' step.  What we see is some controls on the left handside and on the right a mesh of the fetlock joint cut in half by the segmentation plane.  We are going to measure the height of the sagittal ridge.  To do this we must place seven points along the line of ridge at three different segmentation plane angles.  The seven points must define the line forming the base of the plane and the peak of the ridge.  The order that the points are placed on the segmentation plane is not important, however it is important that the segmentation point used to mark the peak of the ridge is the fourth point counted from the left-hand or right-hand side of the plane.  :numref:`dtp_cp_cwf_tsk1_ridge` shows seven points placed on the segmentation plane with the plane angle set at zero degrees.

.. figure:: _images/segmentedridge.png
   :name: dtp_cp_cwf_tsk1_ridge
   :align: center
   :alt: Segmenting the sagittal ridge at 0 degrees
   
   Segmented ridge of fetlock joint at 0 degrees
   
As shown, six points are used to define the base plane of the joint with the innermost segmentation points of the plane used to mark the start of the rise of the ridge.  The middle (or fourth point) is used to mark the peak of the ridge.

For the anaylsis of the ridge we are required to segment the ridge at three different segment plane angles.  The angles that we require are +30 degrees, 0 degrees and -30 degrees.  The process for the segmentation at each plane angle is the same as outlined above.

Once we have completed segmenting the sagittal ridge for the three plane angles we have completed the interactive part of this workflow.  The remaining two steps are the 'Hoof Point Anaylzer' step and the 'Dict Serializer' step.

The 'Hoof Point Analyzer' step takes the segmented data and characterises the hoof throught the height and the angle of the sagittal ridge.  This information is then stored to disk in the 'Dict Serializer' step.

At this point the workflow stops but it could carry on to adding the new measurement to a database of such measurements and from there infer from the analysis some risk of injury for the horse.  The next workflow in this section will show a much more comprehensive and complex physiological modelling cycle. 

Patient Femur Analysis Workflow
===============================

Task two is to execute and follow through a (almost) complete computational physiological cycle.  For this task we will take a set of MR images of the knee joint and some fudicial markers taken from the patient so that we can take a set of measurements that are consistent across all patients and provide data for a clinician to prepare the best treatment for the patient.

In Figure 1 we have the workflow for analysing a patient's femur.  It is a very complex workflow and by far the most advanced that we have seen.  We can of course use this workflow to analyse any bone that we have the required population based principal component model data.  At this time we have this data for all the major bones of the lower limb.

This workflow as previously stated is rather complex, it has a number of interactive steps and non-interactive steps.  The 
