3. gyakorlat - 2017-03-06
1. A feladat megoldásának határideje (eddig várjuk az e-maileket): 2018-03-16 12:00

1. A gyakorlat során létrehozott (vagy az általam megosztott) processzből indulj ki. Hozz létre egy Subprocesst, amelyben kiszámolod az adott klaszterezéshez tartozó Davies–Bouldin indexet.
1. Találd meg a fent létrehozott index szerint a k-means klaszterezéshez tartozó optimális k értéket. (Ehhez segítséget nyújt az általam megosztott Loop operátort is tartalmazó processz.)


1. Ha megtaláltad az ideális k értéket, akkor ezt felhasználva hozz létre egy klaszterezést. A klasztercímkét használd fel, mint célváltozó és erre az adathalmazra taníts rá egy logisztikus regressziós algoritmust. Hogyan lehet értelmezni az így kapott logisztikus regressziós modellt?
1. Küldd át a processzed és a megfigyeléseid a következő címre.


# Kérdések
* Can I calculate Davies Bouldin for hierachical clustering?
* What type of data the regression requires
* Peak minute 10 disappears from the results (but exists among the process outcomes)


# Original flow

## 1. Read CSV

## 2. Data Preparation
### 1. Set role
Attribute `id` role to Cust_ID.

### 2. Select Attributes
Filter out nominal values

### 3. Normalize
Range transformation

### 4. Filter Examples
Dropping missing attributes

### 5. Remove correlated attributes
Remove those attributes of which mutual correlation is above 0.8.

## 3. Outlier Detection
### 1. Cross distances
Finds the 10 nearest cross distance neighbors.

### 2. Aggregates
Group examples by the `request` attribute and calculates their average k-distances.

### 3. Sort
Sorts examples by the distance averages in a decreasing order.

### 4. Filter examples
Filter for examples with average distance less than 0.8

### 5. Select Attributes
Selects the `request` attribute.

### 6. Join
Inner joins the `request` attributes with the original dataset.

## 4. Clustering (K-means)
k = 5
Maximum 5 runs
Bregman Divergences
Squared Euclidean
Max 100 optimization steps

## 5. Clustering (Hierarchical)
Compelete link, Euclidean

## 6. Loop
100 iterations
### 1. Flatten clustering
For each %{iteration}.

### 2. Calculating SSB and SSW
 1. Recieves the flat cluster
 2. Recieves The example set

#### 1. Apply model
 * Applies the cluster on the example set.

#### 2. Generate attribute
 * Creates a `tmp` attribute with "tmp" value.


#### 4. Pivot
Calculates averages for each cluster
 * Group by cluster and calculates average
 * use `tmp` as the index attribute (appends them at the end of the attribute names, e.g. 'age_tmp')
#### 5. Rename by replacement
 * Removes the "tmp" ending
#### 6. Select attribute
 * filters out special attributes (ids, cluster, tmp)


#### 7. Pivot
Calculates attribute averages for the whole set
 * Group by `tmp`
 * calculates averages
 * uses 'tmp' as the index attribute
#### 8. Rename by replacement
 * Removes the "tmp" ending
#### 9. Select attribute
 * filters out special attributes (ids, cluster, tmp)

#### 3. Select attribute
Drops the following values
 * Cluster
 * cluster id
 * tmp
 * id

#### 10. Cross distances
Calculates the distances between cluster averages and the dataset averages
#### 11. Aggregate
Calculates the distance average
#### 12. Rename

#### 10. Cross distances
Calculates the distances between values and their averages for each example
#### 11. Aggregate
Calculates the distance average
#### 12. Rename

#### 13. Cartesian
#### 14. Generate attributes

### 3. Handling exceptions
### 4. Remembering

## 7. Cluster model visualizer
centroid-based cluster visualization

## 8. SSB and SSW calculator
Recives
1. Centroid cluster model
2. Data table

#### 1. Apply model
#### 2. Generate attribute

#### 3. Select attribute

#### 4. Pivot
#### 5. Rename by replacement
#### 6. Select attribute

#### 7. Pivot
#### 8. Rename by replacement
#### 9. Select attribute

#### 10. Cross distances
#### 11. Aggregate
#### 12. Rename

#### 10. Cross distances
#### 11. Aggregate
#### 12. Rename

#### 13. Cartesian
#### 14. Generate attributes

## 9. Recall
recalls tmp ExampleSet
