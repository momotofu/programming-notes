### Vocabulary
Primary Key: a column or columns that uniquely identify what each row is about
Foreign Key AKA a reference constrant: column or columns in one table that uniquily identifies a rows in another table. It's possible for a table to have two or more foriegn keys. A foreign key will usually point to a primary key of another table.

i.e.
```
create table students (
  id serial primary key,
  name text);

create table courses (
  id text primary key,
  name text);
  
create table grades (
  student integer references students(id),
  course text references sourses(id),
  grade text);
```

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
```
4. Tables shouldn't imply relationships that don't actually exist.

i.e. Annabel knows Linux and French, not linux in french.
```
+---------+--------------+----------+
|  name   |  technology  | language |
+---------+--------------+----------+
| Annabel | Databases    | English  |
| Annabel | Linux        | French   |
| Annabel | Data Science | Arabic   |
| Leon    | Data Science | English  |
| Leon    | Windows      | Kurdish  |
+---------+--------------+----------+
```
solution: Map people to tech_skills table and people to language skills
tech_skills:
```
+----------------------+--------------+
|         name         |  technology  |
+----------------------+--------------+
| Annabel Databases    |              |
| Annabel Linux        |              |
| Annabel Data Science |              |
| Leon                 | Data Science |
| Leon                 | Windows      |
+----------------------+--------------+
```
language_skills:
```
+----------+----------+
|   name   | language |
+----------+----------+
| Annabel  | English  |
| Annabel  | French   |
| Annabel  | Arabic   |
| Leon     | English  |
| Leon     | Kurdish  |
+----------+----------+
```
