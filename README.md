# Day 24 – Ride Booking Analysis (Python Coding Challenge)

A beginner-friendly Python data analysis exercise. You play the role of a data analyst at a ride-booking company (like Ola/Uber) and answer questions about a small set of ride records using tuples, loops, and dictionaries.

## Problem Statement

Each ride record is stored as a tuple:

```
(ride_id, driver_name, city, fare, rating)
```

Sample data:

```python
rides = (
    (101, "Ravi",   "Bangalore", 250, 4.5),
    (102, "Anjali", "Hyderabad", 180, 4.2),
    (103, "Kiran",  "Bangalore", 300, 4.8),
    (104, "Meena",  "Chennai",   220, 4.0),
    (105, "Arjun",  "Bangalore", 150, 3.9),
)
```

## Tasks and Results

| # | Task | Result |
|---|------|--------|
| 1 | Count total rides | `5` |
| 2 | Extract all rides from Bangalore | Rides `101`, `103`, `105` |
| 3 | Total revenue from Bangalore | `700` |
| 4 | Highest rated driver | `(103, 'Kiran', 'Bangalore', 300, 4.8)` |
| 5 | Average rating per city | `{'Bangalore': 4.4, 'Hyderabad': 4.2, 'Chennai': 4.0}` |

## Approach

1. **Total rides:** `len(rides)` returns the number of tuples.
2. **Bangalore rides:** loop through `rides` and print each tuple where the city matches.
3. **Bangalore revenue:** accumulate `ride[3]` (the fare) for every Bangalore ride.
4. **Highest rated driver:** collect all ratings (`ride[4]`) into a list, find the max, and use `.index()` to get the matching ride tuple.
5. **Average rating per city:** keep two dictionaries, one for the sum of ratings and one for the ride count per city, using `dict.get(key, 0)`. Divide and `round(..., 1)` to get each city's average.

## Concepts Practiced

- Tuples and nested tuples (indexing, e.g. `ride[2]`)
- `for` loops and `range(len(...))`
- Conditional filtering with `if`
- Aggregation (sum, max, average)
- Dictionaries, `dict.get()`, and dictionary comprehensions
- Built-ins: `len()`, `max()`, `round()`

## Files

- `Day-24-Data-analytics-challenge-python.ipynb`: solution notebook
- `Day24_Coding_Challenge.pdf`: original challenge statement

## How to Run

1. Install Python 3.9+ and Jupyter:
   ```bash
   pip install notebook
   ```
2. Launch Jupyter and open the notebook:
   ```bash
   jupyter notebook Day-24-Data-analytics-challenge-python.ipynb
   ```
3. Run the cells from top to bottom (**Kernel → Restart & Run All**).

## Notes and Possible Improvements

- The Bangalore filter uses `city in rides[i]`, which checks every field of the tuple. It works for this data, but comparing the specific field (`rides[i][2] == city`) is safer and more precise.
- The same tasks can be written more concisely with list comprehensions, `sum()`, and `max(rides, key=lambda r: r[4])`.
- For larger datasets, consider using `pandas` (`groupby`, `mean`, etc.).
