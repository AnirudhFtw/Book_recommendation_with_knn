# 📚 Book Recommendation System (KNN)

## Overview  
This project implements a **Book Recommendation System** using the [Book-Crossings dataset](http://www2.informatik.uni-freiburg.de/~cziegler/BX/), which contains **1.1 million ratings** (scale 1–10) of **270,000 books** by **90,000 users**.  

The system uses the **K-Nearest Neighbors (KNN)** algorithm to recommend books similar to a given book, based on user rating patterns.  

---

## 📂 Dataset  
The Book-Crossings dataset includes:  
- **BX-Books.csv** → Book metadata (ISBN, title, author)  
- **BX-Users.csv** → User IDs & demographics (not used here)  
- **BX-Book-Ratings.csv** → User–book ratings  

---

## 🛠 Data Preparation  
1. **Filtering**  
   - Removed users with fewer than **200 ratings**  
   - Removed books with fewer than **100 ratings**  

2. **Merging**  
   - Ratings merged with book metadata (`isbn → title`)  

3. **Cleaning**  
   - Dropped duplicate titles (keeping first occurrence)  

4. **Matrix Creation**  
   - Built a **book–user rating matrix** (rows = books, columns = users)  
   - Filled missing values with `0`  
   - Converted to a sparse matrix for efficiency  

---

## 🤖 Model  
- **Algorithm**: K-Nearest Neighbors (`sklearn.neighbors.NearestNeighbors`)  
- **Metric**: Cosine distance (measures rating pattern similarity)  
- **Steps**:  
  1. Input a book title  
  2. Locate it in the matrix  
  3. Find top 5 nearest books  
  4. Return list of recommendations with distances  

---

## 📊 Example Output  

```python
get_recommends("The Queen of the Damned (Vampire Chronicles (Paperback))")
