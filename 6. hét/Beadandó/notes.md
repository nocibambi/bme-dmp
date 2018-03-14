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

#### 3. Select attribute
 * Cluster
 * cluster id
 * tmp
 * id

#### 4. Pivot
 * Group by cluster and calculates average
 * use `tmp` as the index attribute
#### 5. Rename by replacement
 * Replaces "tmp"
#### 6. Select attribute
 * filters out special attributes (ids, cluster, tmp)
#### 7. Pivot
 * Group by `tmp`
 * calculates averages
 * uses 'tmp' as the index attribute

#### 8. Rename by replacement
 * Replaces "tmp"

#### 9. Select attribute
 * filters out special attributes (ids, cluster, tmp)

#### 10. Cross distances
#### 11. Aggregate
#### 12. Rename

#### 10. Cross distances
#### 11. Aggregate
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
