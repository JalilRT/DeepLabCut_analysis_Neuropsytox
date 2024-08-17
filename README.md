# Behavior analysis tutorial

Another short tutorial of HOW TO NEUROPSYTOX:

- [Behavior analysis tutorial](#behavior-analysis-tutorial)
- [Installation](#installation)
    - [DeepLabCut (already installed in laboratory laptops)](#deeplabcut-already-installed-in-laboratory-laptops)
- [Running DLC for animal tracking](#running-dlc-for-animal-tracking)
  - [DeepLabCut to analyze videos of EPM or NOR](#deeplabcut-to-analyze-videos-of-epm-or-nor)
    - [Re-train your network](#re-train-your-network)
- [Behavior metrics](#behavior-metrics)
    - [Using the shiny app to run DLCAnalyzer scripts](#using-the-shiny-app-to-run-dlcanalyzer-scripts)
- [Assistent watchers to create ethograms](#assistent-watchers-to-create-ethograms)
  - [Using BORIS](#using-boris)
- [Discovering behaviors (pose + frame networks)](#discovering-behaviors-pose--frame-networks)

# Installation 

### DeepLabCut (already installed in laboratory laptops)

1. By hand:
   1. Install Python 3.7 or higher.
   2. Install DeepLabCut using pip: `pip install deeplabcut[gui]`.
2. Through anaconda yalm file
   1. Install anaconda environments
   2. Create a new environment: conda create -n my_env python=3.7.
   3. Activate the environment: conda activate my_env.
   4. Install DeepLabCut using conda: conda install -c conda-forge deeplabcut.
   5. Install additional dependencies: pip install deeplabcut[gui].
   6. Verify the installation: deeplabcut check-requirements.

   ![alt text](image.png)
   7. Install anaconda environments
   ![alt text](image-1.png)
   8. git clone https://github.com/DeepLabCut/DeepLabCut.git or download as a zip file
   9. Open the Anaconda Navigator
   10. Select the yalm file and install it 
   ![alt text](image-2.png)
   11. After installing, run ipython terminal
   ![alt text](image-3.png)
   12. Run:
       1.  Import deeplabcut
       2.  Run deeplabcut.launch()
   ![alt text](image-4.png)
   13. Open DLC gui
   ![alt text](image-5.png)


**Links** 📖:
https://deeplabcut.github.io/DeepLabCut/docs/installation.html

# Running DLC for animal tracking
## DeepLabCut to analyze videos of EPM or NOR

1. Import library `import deeplabcut`
2. Launch the gui: `deeplabcut.launch_dlc()`
   ![alt text](image-6.png)
3. Open the config file with `Load project`
   1. EPM
   ![alt text](image-9.png)
   2. NOR
   ![alt text](image-8.png)

4. To analyze videos, first you must have your videos cropped and/or with a compression (reduce the resolution)
   1. If not, use the DLC tool
   
   ![alt text](image-10.png)
   ![alt text](image-11.png)
   2. Just click crop as many videos you have 
   3. Also, you can rotate or flip your videos
   4. If is borring to click, you can do it with a script by using ffmpeg (-crf to adjust the resolution, higher is low res):
    `ffmpeg -i input.mp4 -vcodec libx265 -crf 28 input_cropped.mp4`
5. You can now analyze your videos with just one-click, remember to allow the save as csv option
   ![alt text](image-12.png)
6. You can see the progress on the terminal
   ![alt text](image-13.png)
7. For quality control, is highly recommendable to view some videos of each batch to be sure that the network is predicting your animal (mouse or rat) pose and the maze. To do that, just click on create videos tab and in the button.
   ![alt text](image-14.png)
8. Your animals are tracked! You can work with the coordinates in the best way you want to (see Behavior metrics or Discovering behaviors).
   ![alt text](image-15.png)
9. You will have 3 more files:
   1.  coordinates csv
   2.  python datafile (h5)
   3.  python metadata
   ![alt text](image-17.png)
   ![alt text](image-16.png)

### Re-train your network
If the pose DLC or NOR -network is doing a terrible job to tracking, you can re-train it using your own videos. 

1. Use a few videos to re-train (maybe 4 per recording conditions).
2. You have to re-label, in total would be 5 frames per video.
3. Extracting outliers.
4. Re-label.
5. Re-training the network
6. Analyze and quality control (See above section)

# Behavior metrics
### Using the shiny app to run DLCAnalyzer scripts
Please read the [paper](https://www.nature.com/articles/s41386-020-0776-y) and check the github repository: https://github.com/ETHZ-INS/DLCAnalyzer

Based on those scripts i built a quick shiny app to run the scripts by GUI

1. Open RStudio
   ![alt text](image-18.png)
2. Load the app file
   ![alt text](image-19.png)
3. Just run the app
   ![alt text](image-20.png)
4. It will open the GUI
   ![alt text](image-22.png)
5. Fill the inputs
6. Add the input directory, the files are the coordinates in csv obtained by DLC
   ![alt text](image-23.png)
7. Load the zoneinfo file from EPM or NOR
   ![alt text](image-24.png)
8. Fill the frames of your videos, all csv files must have been obtained from videos with the same fps, you can check it by see the videos details
   ![alt text](image-26.png)
9. Fill the options, you can allow the export option to create the excel table
   ![alt text](image-27.png)
10. Metrics are ready for each csv file!
   ![alt text](image-28.png)
   ![alt text](image-33.png)
11. You can explore the metrics based on demographics, just upload it and click submit
   ![alt text](image-29.png)
    1.  The first column must be each csv filename, with "file" as first row
    2.  The rest could be as you want
        ![alt text](image-31.png)
12. You will see the same table as before, but now, in the graph tab you can create different visualization of the metrics and demographics, select the Y,X,Z that you're interested.
   ![alt text](image-30.png)
13. At the end, you will have the indexes file with all basic DLCAnalyzer metrics
   ![alt text](image-32.png)

# Assistent watchers to create ethograms
## Using BORIS

# Discovering behaviors (pose + frame networks)





