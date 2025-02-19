# Altscore Challenge - s1e10

### Frame the problem & Look at the big picture

**Predict *`cost_of_living`* in the Empire considering:**

- train.csv: hex_id // cost_of_living
Data from sectors already liberated by the Rebellion. Each entry contains precise coordinates and the true cost of living, encrypted by the Galactic Council's H3 technology.

- test.csv: hex_id // cost_of_living
Sectors still under Imperial control, awaiting your predictions to reveal the hidden cost of living.

- mobility.parquet: device_id // lat // lon // timestamp
 A data set containing the secret movement patterns of operatives, smugglers, and civilians across the galaxy. These movements hold the clues to understanding the local economies of each region.

**What can we obtain from datasets?**
1. From lat/lon we can obtain hex_id via h3 package using *`resolution = 8`*.
2. Per hex_id obtain an "area" of the hex using Polygon *`hex_area_df`*.
3. Devices per hex_id.
4. Readings per hex_id.
5. Times in which readings are taken.
6. data/no-data from mobility to train

**What can affect the cost_of_living at first sight?**
1. Unique devices per hex (population).
    -   Get hex where device got most recordings?
2. Devices that visit an hex.
3. Define an hex connectivity measurement.
4. Square km of each hex.
5. From enunciate we could try figure movement of empire_operatives, smugglers and civilians using device_id and timestamp.
    -   Days, hours of movement
    -   (Unsupervised learning: k-means, GMM, DBSCAN?)

**Missing Data handling**
1. 1/0 if hex data existed on mobility
2. Use hex neighbors to get data into non existent mobility hex
3. What if no neightbors around?


