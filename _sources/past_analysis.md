# Analysis on this data

To study the neural basis of decision-making in primary auditory cortex (A1), we trained 9 transgenic CBA x Thy1-GCaMP6s F1 mice to perform a pure-tone frequency discrimination task during in vivo 2-photon (2P) Ca2+ imaging experiments in A1. Head-fixed mice were trained to lick a waterspout in response to a low-frequency target tone (7 or 9.9 kHz, red), and to avoid licking the waterspout after hearing a high-frequency non-target tone (14 or 19.8 kHz, 88 blue). The four frequencies were randomized across trials. The mice were trained to withhold behavioral responses for 0.5 s after the onset of a target tone in order to receive the reward of a water droplet. This waiting period enabled us to assess neural responses before the animal indicated its decision. Each trial’s behavioral response was categorized as a hit (licking after target onset), miss (no licking after a target), false alarm (licking after non-target onset), or correct rejection (no licking in response to a non-target). Incorrect behavioral responses were punished with an 8 s time-out added to the ITI.

The experiment has total 34 sessions of nine animals( 3 female, 6 male ). The different sessions are performed on different days.  
![alt tag](https://user-images.githubusercontent.com/57324666/89909399-06f14b00-dbbd-11ea-9e09-86a9f660d2db.png) 
                                             
                                             Figure 1: Strcuture of the Data (bottom to up)



The dataset we are working with contained response amplitude (delta F/F traces) of neurons (np 3d: time x k_trials x k_neurons), neuron locations (np 2d: k_neurons x 2 [x,y]), lick traces (np 2d: time x k_trials) and responsive and bright cells during the trials. 

Average number of trials for each condition (across sessions and animals)

![alt tag](https://user-images.githubusercontent.com/57324666/89362373-cb75ee80-d69b-11ea-9f62-d9fbf6f521e4.png)

                                                     Figure 2: Average number of trials
                                                     


To visualize lick traces, values were averaged across trials (for each animal).

![alt tag](https://user-images.githubusercontent.com/57324666/89362486-06782200-d69c-11ea-9301-036973dd7ebd.jpg)

                                                       Figure 3:lick traces (The auditory tone was presented between the two vertical lines in the heat map)
                                                       
 The cells (only non-nans cells) which are responsive in both passive and behavior trials are kept. 
 
 - some cells are showing very high responses in comparison to other responsive cells.
 - we compute median and standard deviation for each experiment (across trials, time and cells).  
 - if a cell’s max response for any trial is greater than median + 10\times standard deviation, that cell is removed.
 
To remove the bright cells which are showing very high outlier responses 
- a cell’s absolute max response for every trial is calculated. 
- If for any trial it is greater than K SDs (the value has been chosen by experimenting), then that cell is removed. 
- For k SDs = 15, 90% of the neurons retained, so we chose that value to work with.                                                     

To visualize the response amplitude of each cell, the calcium traces were averaged across trials (for each cell for each trial condition). 

![alt tag](https://user-images.githubusercontent.com/57324666/89362734-9d44de80-d69c-11ea-9a45-b38a62076c6f.jpg)

                                   Figure 4: delta F/F traces for responsive cells (after removing outlier responses (3b)) 

![alt tag](https://user-images.githubusercontent.com/57324666/89362991-222ff800-d69d-11ea-8d66-6d2a68490666.jpg)

                                   Figure 5 : delta F/F traces for responsive cells (  z-scored delta F/F traces after removing outlier responses (3c))
                                   
![alt tag](https://user-images.githubusercontent.com/57324666/90155142-faa1f500-dd58-11ea-9437-1b8abf526c1c.png) 

                                  Figure 6 : delta F/F traces for bright cells ( z-scored delta F/F traces without removing outlier responses(3e))

![alt tag](https://user-images.githubusercontent.com/57324666/89363051-4ab7f200-d69d-11ea-9d1b-16c90ef2529a.jpg)
                                              
                                   Figure 7 : delta F/F traces for bright cells ( z-scored delta F/F traces after removing outlier responses(3d))

# PCA Analysis
For three highest variance components the trajectories are plotted below in order of the trial sequences. 

![alt tag](https://user-images.githubusercontent.com/57324666/89363239-b39f6a00-d69d-11ea-8faf-58ae51afa210.jpg)
                                            
                                    Figure 7: trajectories of three highest variance components
                                           
Then for each trial type mean of all trajectories (a mean trajectory for hit, miss, etc) are plotted.
![alt tag](https://user-images.githubusercontent.com/57324666/89363606-9f0fa180-d69e-11ea-8bf0-debcec388c7d.jpg)
                                            
                                            Figure 8: Mean trajectories for all trial types
 
 To see if any of the principal components are highly correlated with lick traces, five high variance components are plotted in full time series.                                
![alt tag](https://user-images.githubusercontent.com/57324666/89363612-a171fb80-d69e-11ea-8f6f-d4e528ecbd39.jpg)

                                           Figure 9: Correlation of lick traces with principal components
                                          
Then the Pearson correlation coefficient and p-value for testing non-correlation is calculated between the lick traces and principal components.    

![alt tag](https://user-images.githubusercontent.com/57324666/89363666-bd759d00-d69e-11ea-9127-0e84e70abe63.jpg)
![alt tag](https://user-images.githubusercontent.com/57324666/89363667-be0e3380-d69e-11ea-92fb-5caa252a994f.jpg)

                                           Figure 10 : Correlate pcs with lick trace
                                           
![alt tag](https://user-images.githubusercontent.com/57324666/89363669-be0e3380-d69e-11ea-8e4b-40da10be1c2f.jpg)
                                          
                                          Figure 11: Color coded correlation of lick traces with principal components
                                          
Reference: Manasij Venkatesh
