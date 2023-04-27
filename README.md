# age-model-interpolation-function
Interpolate ages for a given isotope stratigraphy dataset based on an age model of tie points.

Arguments:
data_file: Name of the .txt file containing the dataset. Data file must have column order: 
depth, d13C, d18O. Column headers cannot contain spaces.
age_model_file: Name of the .txt file containing the age model. Age model file must have column order:
depth, age. Column headers cannot contain spaces.

Returns:
datall: Dataframe containing the original dataset with interpolated ages. Column order:
depth, age, d13C, d18O.
datave: Dataframe containing averaged data and interpolated ages. Column order:
depth, age, d18O_mean, d18O_std, d18O_se, d13C_mean, d13C_std, d13C_se, count.


## Background

The δ18O stratigraphy of sediment cores is a powerful tool for learning about Earth’s prehistoric climate; before modern humans were around and/or capable of recording detailed measurements for themselves.

δ18O is a stable isotope that is measured through the analysis of tiny single celled organisms called foraminifera. As foraminifera grow, they incorporate ions from the surrounding seawater into their shells, including the δ18O signature of that water. When they die, their shells fall through the water column and over time, accumulate in sedimentary layers on the seafloor.

Analysis of δ18O is insightful for studying climate because its composition in seawater varies as a direct result of changes in global temperature and ice volume. However, in order to accurately interpret δ18O values from sediment cores in the context of Earth’s history, we need to know the date in time that each sedimentary layer was deposited. Complicating this process, is that sedimentary layers are not deposited at a constant rate. Instead, sedimentation rate can vary significantly throughout time due to changes in factors such as changing ocean currents and sea level. Luckily, tools like radiocarbon analysis and alignment to global reference data can help to assign some ages to specific depths throughout a sediment core, constructing what is known as an age model. For everything in between, an interpolation function can be useful for filling in missing ages based off of the tie points that we know.

Here I develop a function that interpolates ages for a given isotope stratigraphy dataset based on an age model of tie points. The function also produces some summary statistics for depths with multiple samples. Through plotting the results, we can examine a history of Earth’s climate over the last 150,000 years, which spans the last glacial cycle. This record is conveniently plotted with time on the x axis rather than depth, made possible by this age model interpolation function.


Dataset citations:  
Channell, J. E. T., Hodell, D. A., & Lehman, B. (1997). Relative geomagnetic paleointensity and δ18O at ODP Site 983 (Gardar Drift, North Atlantic) since 350 ka. Earth and Planetary Science Letters, 153(1–2), 103–118. https://doi.org/10.1016/s0012-821x(97)00164-7

Raymo, M. E., Oppo, D. W., Flower, B. P., Hodell, D. A., McManus, J. F., Venz, K. A., Kleiven, K. F., & McIntyre, K. (2004). Stability of North Atlantic water masses in face of pronounced climate variability during the Pleistocene. Paleoceanography, 19(2), 1–13. https://doi.org/10.1029/2003PA000921

## Required packages
- numpy
- pandas
- matplotlib.pyplot
- scipy.interpolate
