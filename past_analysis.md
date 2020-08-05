# 2.Past analysis on this data
# Data in .mat file
The structure arrays in the .mat file of each mouse participated in the experiment named behavior and passive. The behavior structure array contained mouse name, experiment date, delta F/F traces smoothed and corrected (response amplitude) (np 3d: time x k_trials x k_neurons), neuron locations (np 2d: k_neurons x 2 [x,y]), responsive_cells,  bright_cells, frames per second, first lick during a trial (one-hot np 2d: time x k_trials), lick traces for 'target' frequency (one-hot np 2d: time x k_trials) lick traces for 'nontarget' frequency (one-hot np 2d: time x k_trials). If first response is between early window onset and early window offset that trial is categorized with an early tag. But if first response is between response window onset and response window offset, that trial is eligible for reward tag. 

# Pickling in python

In the 00-mat2pkl.py the picking is done on the provided .mat files. After that cells (only non-nans cells) which are responsive in both passive and behavior trials are kept in 01-save responsive.py. Still, some cells are showing bizarre (very high) responses in comparison to other responsive cells. That’s why compute median and standard deviation for each experiment (across trials, time and cells) were computed in 01b-clean_responsive. Then, if a cell's max response for any trial is greater than median + 10*standard deviation, that cell is removed.

The standard score (more commonly referred to as a z-score) is a very useful statistic because it allows us to calculate the probability of a score occurring within our normal distribution and enables us to compare two scores that are from different normal distributions. In 01c-clean_zscore_responsive.py file, the z-scored delta F/F traces are saved. 

In 01d-save_bright.py file, we worked with bright cells. Cells which were bright in both passive and behavior trials are kept, bright cells which have nan responses were removed. The z-scored delta F/F traces are saved in 01e-zscore_bright.py file. To remove the cells which are showing bizarre responses (very high), a cell's absolute max response for every trial is calculated. If for any trial it is greater than k*standard deviation, then that cell is removed. For k*standard deviation=15, 90% of the neurons retained, so we chose that value to work with. 

# Visulaizing behavior

In 02-visualize behavior.py, for each condition, 'hit', 'miss', 'falsealarm' and 'correctreject’, for first ten cell calcium traces and lick traces are averaged across trials for each experiment and displayed in figures. 


![alt tag](https://user-images.githubusercontent.com/57324666/89362031-cb292380-d69a-11ea-96e2-d8f28d5e6c89.jpg)

                                                     Figure: Visualizing behavior

In 02b-visualize_behavior_stats.py file, we visualize the number of cells in the bright_z-scored_files and responsive (01_save responsive.py) files. 
Average number of trials for each condition is calculated in 03b-visualize_behavior_mean_clean.py file. 

![alt tag](https://user-images.githubusercontent.com/57324666/89362373-cb75ee80-d69b-11ea-9f62-d9fbf6f521e4.png)

                                                     Figure: Average number of trials

Then, for each condition to visualize lick traces, lick traces are averaged across trials for each experiment. The auditory tone was presented between the two vertical lines. 

![alt tag](https://user-images.githubusercontent.com/57324666/89362486-06782200-d69c-11ea-9301-036973dd7ebd.jpg)

                                                       Figure:lick traces

To visualize delta F/F traces first the traces are averaged across trials for each cell for condition of interest. 

![alt tag](https://user-images.githubusercontent.com/57324666/89362734-9d44de80-d69c-11ea-9a45-b38a62076c6f.jpg)

                                                   Figure: delta F/F traces for clean files (3b)

![alt tag](https://user-images.githubusercontent.com/57324666/89362991-222ff800-d69d-11ea-8d66-6d2a68490666.jpg)

                                               Figure: delta F/F traces for responsive clean z-score files (3c)

![alt tag](https://user-images.githubusercontent.com/57324666/89363051-4ab7f200-d69d-11ea-9d1b-16c90ef2529a.jpg)
                                              
                                               Figure: delta F/F traces for bright clean z-score files (3d)
# PCA (principal component analysis)

For three highest variance components the trajectories are plotted in order of the trial sequences. 

![alt tag](https://user-images.githubusercontent.com/57324666/89363239-b39f6a00-d69d-11ea-8faf-58ae51afa210.jpg)
                                            
                                            Figure: trajectories of three highest variance components
                                           
Then for each trial type mean of all trajectories (a mean trajectory for hit, miss, etc) are plotted.
![alt tag](https://user-images.githubusercontent.com/57324666/89363606-9f0fa180-d69e-11ea-8bf0-debcec388c7d.jpg)
                                            
                                            Figure: Mean trajectories for all trial types
 
 To see if any of the principal components are highly correlated with lick traces, five high variance components are plotted in full time series.                                
![alt tag](https://user-images.githubusercontent.com/57324666/89363612-a171fb80-d69e-11ea-8f6f-d4e528ecbd39.jpg)

                                           Figure: Correlation of lick traces with principal components
                                          
Then the Pearson correlation coefficient and p-value for testing non-correlation is calculated between the lick traces and principal components.    

![alt tag](https://user-images.githubusercontent.com/57324666/89363666-bd759d00-d69e-11ea-9127-0e84e70abe63.jpg)
![alt tag](https://user-images.githubusercontent.com/57324666/89363667-be0e3380-d69e-11ea-92fb-5caa252a994f.jpg)

                                           Figure: Correlate pcs with lick trace
                                           
![alt tag](https://user-images.githubusercontent.com/57324666/89363669-be0e3380-d69e-11ea-8e4b-40da10be1c2f.jpg)
                                          
                                          Figure: Color coded correlation of lick traces with principal components
