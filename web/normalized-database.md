### Constraints
1. Every row has the same number of columns
2. There is a unique **key** in each row, and every column in that row says something about the key. In any row the key provides the topic of the sentence that the rest of the row says something about.

  Below: part_num is the key. Color, material, and shape describe the numbered parts.
  ```
  +----------+--------+----------+--------+
  | part_num | color  | material | shape  |
  +----------+--------+----------+--------+
  |      413 | green  | plastic  | cube   |
  |     1203 | black  | iron     | gear   |
  |     9512 | pink   | glass    | bottle |
  |    10101 | yellow | amber    | lump   |
  +----------+--------+----------+--------+
  ```
3. Facts that don't relate to the key belong to different tables.

#### Bad example: address relates to location
items
```
+-------------+-------+------------+-----------------+
|    item     | count | location   |     address     |
+-------------+-------+------------+-----------------+
| rubber duck |    43 | Toy Mart   | 123 Quacker Rd. |
| tennis ball |   117 | Toy Mart   | 123 Quacker Rd. |
| mutant cat  |    27 | Secret Lab | 1 Rainbow Falls |
| wifi hub    |    64 | Secret Lab | 1 Rainbow Falls |
+-------------+-------+------------+-----------------+
```

#### Solution: split out address into its own table.
items
```
+-------------+-------+------------+
|    item     | count |  location  |
+-------------+-------+------------+
| rubber duck |    43 | Toy Mart   |
| tennis ball |   117 | Toy Mart   |
| mutant cat  |    27 | Secret Lab |
| wifi hub    |    64 | Secret Lab |
+-------------+-------+------------+
```
locations
```
+------------+-----------------+
|  location  |     address     |
+------------+-----------------+
| Toy Mart   | 123 Quacker Rd. |
| Toy Mart   | 123 Quacker Rd. |
| Secret Lab | 1 Rainbow Falls |
| Secret Lab | 1 Rainbow Falls |
+------------+-----------------+
