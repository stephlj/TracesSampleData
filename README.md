# Sample smFRET data for the Traces analysis suite

Sample data to accompany the single-molecule FRET analysis software [Traces](https://github.com/stephlj/Traces).

NOTE: Total repository size is roughly 3 GB, including all raw files and analysis files.

# Analyzing this sample data with Traces

To run the Traces analysis from the very beginning, including making a channel map, run (in the Matlab command line)

```matlab
Traces('SNF2h51nMATP1mM')
```

and press enter when prompted in the command line. 

To use the channel map provided in ChannelMapping.mat, run the same command to Traces as above, but type L (caps insensitive) and then enter when prompted. Navigate to the directory with this sample data (which should contain a ChannelMapping.m file), and follow the instructions in the Traces manual to continue.

To load the analysis files provided in this repository, in order to view the data, already processed, in the Traces GUI:

1. Copy Analysis_Files/Traces_Output/SNF2h51nMATP1mM to the directory indicated by defaultsavedir in TracesSetup.m.

2. Run the Traces command as above, choosing L to load a previously generated channel map as before. 

3. Type y and then enter when advised that the save directory already exists.

4. Type n and enter when asked whether to load previously found spots and their intensities.

5. Type y and enter when asked whether to load previously found spots.

6. Type y and enter when asked whether to use the same channel mapping as last time.

To run the pyhsmm HMM analysis on a selection of trajectories saved from this data set:

1. In the config.py file in Traces/extras/pyhsmm_for_Traces, change datadir to point to wherever the output files of Traces (Spot1_51.mat, etc) are. Sample results can be found in AnalysisFiles/pyhsmm_Input in this repo. Also set resultsdir appropriately.

2. In ExamineHMMresults.m, find the calls to setenv and change those lines to point to the location of your python installation.

3. ExamineHMMresults uses a text file called goodtraces to crop data and exclude traces from analysis. A template goodtraces.txt file is included in Traces/extras/pyhsmm_for_Traces. An example that goes with the sample data in this repo can be found in AnalysisFiles/pyshmm_Output/SNF2h51nMATP1mM_analyzed. 

From the Traces/extras/physmm_for_Traces directory (or whatever directory contains ExamineHMMresults.m), run

```matlab
ExamineHMMresults('SNF2h51nMATP1mM_analyzed')
```

The AnalysisFiles/pyshmm_Output/SNF2h51nMATP1mM_analyzed directory contains the files generated by a call to ExamineHMMresults, so you will be prompted whether or not to re-run the pyhsmm analysis from the command line. Remove all but the goodtraecs.txt file to start from the beginning.

Copyright (c) 2017 Stephanie Johnson. The data in this repository is licensed under a [Creative Commons Attribution 4.0 International License](http://creativecommons.org/licenses/by/4.0/).