# Data Model Explanation

This project follows a proper Star Schema modeling approach in Power BI.

## Tables

### Dim_Fighters (Dimension Table)
Contains static attributes of fighters:
- Name, Nickname, Country
- Height, Reach, Sex
- Weight Division, Champion Status, Tier
- fighter_id (Primary Key)
- num_fighter_id (only used for ranking logic)

### Fact_FighterStats (Fact Table)
Contains aggregated performance metrics:
- Number of Wins, Losses, Draws
- Total KO, Submission, Decision wins
- Total Strikes, Takedowns, Knockdowns, Submission Attempts
- Relative Points used for ranking
- fighter_id (Foreign Key)

### Dim_RankSelector (Helper Dimension)
A generated series from 1 to 3405 used to dynamically select fighters by rank for the profile page.

### _Measures Table
Contains all DAX measures, grouped into:
- Card Measures
- Ranking and Filtering Logic

## Relationships

Fighters (1) → Fighter Stats (*)

Rank Selector is disconnected and used purely for dynamic ranking logic via measures.
_Measures is also disconnected, and only used for storing Card and Ranking Logic measures. 