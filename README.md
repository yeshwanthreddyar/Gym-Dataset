# Gym Performance Analysis (2021–2025)

An Excel workbook analysing five years of gym visit records: membership mix, workout popularity, revenue growth, member demographics and customer ratings. All dashboard figures are live formulas over the raw data sheet.

## Dataset at a glance

| Metric | Value |
|---|---|
| Visit records | 10,000 |
| Unique members (by `Member_ID`) | 1,198 |
| Date range | 11-01-2021 to 30-12-2025 |
| Total revenue | ₹23,766,500 |
| Average revenue per visit | ₹2,376.65 |
| Average rating | 3.88 / 5 |
| Average visits per member | about 8.3 |
| Premium visit share | 19.1% |
| Trainer-assisted share | 35.0% |

## Workbook structure

| Sheet | Contents |
|---|---|
| `KPI_Dashboard` | Headline KPIs plus monthly trend (2021–2025), membership, workout, age group, gender and rating breakdowns |
| `Summary` | Five-year totals and a yearly breakdown (visits, revenue, average rating) |
| `Gym_Data` | Raw data: 10,000 rows × 15 columns |

## Data dictionary (`Gym_Data`)

| Column | Description |
|---|---|
| `Member_ID` | Member identifier (`MEM00001` format) |
| `Member_Name` | Member name (not unique per ID) |
| `Age` | Age in years (16 to 64) |
| `Gender` | Male or Female |
| `Membership_Type` | Basic, Standard or Premium |
| `Join_Date` | Date the member joined |
| `Visit_Date` | Date of the visit |
| `Visit_Time` | Time of the visit (HH:MM) |
| `Workout_Type` | Cardio, Strength Training, Yoga, CrossFit, Zumba, Swimming, Pilates or HIIT |
| `Duration_Minutes` | Session length (15 to 130 min) |
| `Calories_Burned` | Calories burned (60 to 1,098) |
| `Trainer_Assigned` | Whether a trainer assisted (Yes or No) |
| `Rating` | Visit rating from 1 to 5 |
| `Payment_Method` | Net Banking, Cash, Credit Card, UPI or Debit Card |
| `Amount_Paid` | Amount charged for the visit (₹) |

## Key findings

- **Strong growth:** visits rose from 180 in 2021 to 5,259 in 2025, and revenue from ₹4.4 lakh to ₹1.24 crore.
- **Membership mix:** Basic (40.9%) and Standard (40.0%) dominate visits. Premium is 19.1% of visits but earns ₹76.3 lakh at ₹4,000 per visit.
- **Revenue by tier:** Standard contributes the most (₹99.9 lakh), followed by Premium and Basic (₹61.4 lakh).
- **Workouts:** popularity is evenly spread. Pilates (1,321 visits), Strength Training (1,282) and Cardio (1,256) lead slightly.
- **Satisfaction:** 70% of visits are rated 4 or 5. Average ratings are similar across workout types (3.82 to 3.92).
- **Payments:** spread almost evenly across five methods, with Net Banking marginally ahead.
- **Demographics:** 52% male and 48% female visits, with an average age of about 41.

## Data notes and limitations

- `Amount_Paid` is a fixed per-visit price by tier (Basic ₹1,500, Standard ₹2,500, Premium ₹4,000), so revenue is effectively visits × tier price.
- There are 1,198 unique member IDs but only 617 unique names, so names do not identify members reliably. Names and genders sometimes look mismatched, which suggests synthetic data.
- No missing values or duplicate rows were found.
- Dates in `Gym_Data` are stored as text (`YYYY-MM-DD`). The dashboard formulas use `YEAR()` on them, which works in Excel but is worth converting to real dates for pivoting.
- Because yearly volume grows sharply, year-over-year totals reflect membership growth, not just per-member spending.

## How to use

1. Open the workbook in Excel.
2. Start at `KPI_Dashboard` for the overview, or `Summary` for yearly totals.
3. To add data, append rows to `Gym_Data`. Formulas reference rows 2 to 10001, so extend those ranges for new rows.
4. The unique-member count uses `SUMPRODUCT(1/COUNTIF(...))`, which can be slow on large data. Consider replacing it with `UNIQUE` in Excel 365.

## Tools

Microsoft Excel: `SUMIF(S)`, `COUNTIF(S)`, `AVERAGEIF`, `SUMPRODUCT` and `IFERROR`.

## Possible next steps

- Analyse member retention and visit frequency by join cohort.
- Study peak hours and days from `Visit_Time` and `Visit_Date`.
- Compare ratings with and without a trainer.
- Add charts or pivot tables to the dashboard.

## Author

Yeshwanth
