The following repository contains the series of Python data fits I have created through my participation with ERAU's Coherent CAPTAIN Mills (CCM) detector research group. I was responsible for measuring the 
kinetic energy spectrum of Michel electrons arising from stopping cosmic muons decaying in the CCM detector. The energy spectrum is to be used to perform calibrations for the search for Light Dark Matter particles.
Each fit in the repository is designed for a specific data set produced by Los Alamos National Laboratory and involves the production of two graphs. Producing these graphs involves the following equation:
<img width="780" height="167" alt="image" src="https://github.com/user-attachments/assets/4b46d77e-533d-4c64-8909-74d7d1ef6e87" />

This function was used to fit the data and identify the local maxima. f(t) was the pulse as a function of time, t_0 was the time the highest peak on the graph emerged (the point of a particle decay) in 
nanoseconds (ns), t was the time in ns, t_s was the singlet time in ns, t_t was the triplet time in ns, c was a constant of 0, theta was a function represented by numpy heaviside, and scalars a and b were used to 
convert the value to a pulse. 
Graphs for muon_data_128 are shown below as an example:
<img width="574" height="413" alt="download" src="https://github.com/user-attachments/assets/8087af89-fcf8-4e81-badb-cdfff01b2268" />


This graph shows the expected kinetic energy spectrum when t_t was assumed to be 743 ns. 

<img width="574" height="413" alt="download" src="https://github.com/user-attachments/assets/f51f7606-1e64-402b-a672-2dfc74a5454d" />

This graph shows the expected kinetic energy spectrum when t_t was fitted with all other parameters (a, b, t_s) using scipy.curvefit. The red line in both graphs is used to calibrate the data to account for 
background noise and accurately integrate the area under the curve to calculate the number of photoelectrons (PE). To acquire graphs like these, you would use csv.reader to record the time and pulse data from the 
text files and convert them to float arrays. Then you would use numpy max and index methods to acquire the first peak in each data set. You would repeat this step to find the second peak by using the previous methods
to find a local maximum succeeding the first one. Define a function based on the above equation and fit it to find the appropriate parameters for a, b, t_s, and t_t (depending on which graph you want to create).
Once you find your parameters, plot them using matplotlib. You will need to create a for loop statement to find t_0 and when the second peak begins to rise to calculate the number of PEs. After finding these values,
you will integrate with 20 and 45 bins to find the range of PEs present in the spectrum. The integration is done by summing the difference between the measured pulse and the sum of the singlet and triplet times across
all bins. 
Note: most of this was done with brute force. 



