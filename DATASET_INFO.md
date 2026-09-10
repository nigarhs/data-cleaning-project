# 🕵️ Crime Data Cleaning Project

Turning a messy, real-world-style crime incident dataset into a clean, analysis-ready one — using Python and pandas.

## 📌 Overview

This project takes a raw dataset of **5,250 crime incident records across 33 columns**, riddled with the kind of chaos you'd actually find in the wild: typos, missing values, mismatched formats, and inconsistent categories. The goal was to clean it into something trustworthy enough to actually analyze.

## 🧩 The Mess I Started With

|Problem|Example|
|-|-|
|Missing values|Up to 1,601 missing values in a single column (`suspect\_race`)|
|Misspelled categories|`Asslt`, `Homocide`, `Domestc Violence`, `Vandlism`|
|Inconsistent casing|`'ga'`, `'Ga'`, `'GA'` all meaning the same state|
|Mixed abbreviations|`'Sou'`, `'South'`, `'southeast'` all describing districts|
|Numbers mixed with text|`severity` had both `1, 2, 3, 4` AND `Low, Medium, High, Critical`|
|Inconsistent booleans|`reported\_online` had `True/False`, `Yes/No`, AND `1/0`|
|Mixed phone formats|`6223265920` vs `241-973-4826`|
|Multiple date formats|ISO (`2024-04-16 08:45:03`), DD-MM-YYYY (`26-08-2022`), and MM/DD/YYYY (`04/29/2020 08:17`) — all in the same column|

## 🛠️ What I Did

1. **Missing values** — Applied targeted strategies per column: median imputation for numeric fields (`latitude`, `longitude`, `victim\_age`), `'Unknown'` placeholders for categorical fields, and row removal only where critical fields (like `incident\_datetime`) were missing.
2. **Duplicates** — Checked for exact duplicate rows (found: 0) and near-duplicates on key fields like date, address, and crime type (found: 46, manually reviewed).
3. **Category standardization** — Built mapping dictionaries to collapse dozens of spelling variants into clean, consistent categories (e.g. 17 messy `crime\_type` variants → 17 standardized labels; district abbreviations → 10 clean district names).
4. **Format normalization** — Standardized state codes, city names, gender labels, phone number formatting, and boolean-style fields into single consistent formats.
5. **Date parsing** — Detected and separately parsed three distinct date formats mixed within one column, reconstructing a single reliable `datetime64` column with zero data loss.

## 📈 Before → After

* **33 columns**, all missing values resolved
* **17 crime type categories** cleaned from 60+ raw spelling/casing variants
* **10 standardized districts** from a mix of abbreviations and full names
* **1 unified datetime format** recovered from 3 conflicting formats
* **0 data loss** on the datetime column despite the format chaos

## 🧰 Tools Used

* Python
* pandas
* Jupyter Notebook

## 📂 Files

* `crime\_incidents\_messy.csv` — the original raw dataset
* `messy-crime-project.ipynb` — full cleaning notebook, step by step
* `crime\_data\_cleaned.csv` — the final cleaned output
* `DATASET\_INFO.md` — the original dataset creator's documentation, describing the raw data's structure and intended use before any cleaning was done



