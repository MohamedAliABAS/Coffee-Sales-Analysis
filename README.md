I worked on a coffee machine sales analysis project using Excel. I wanted to understand how sales were going,
what types of coffee customers preferred, their visit times, payment methods, and the performance of each machine.
I started by cleaning the data in Power Query, adjusting the date and time, and combining the data for each machine into a single sheet so that each machine contained separate data.
Before that, I added a "Card" column to the other machine's data, as it didn't have a "Card" column, so I could combine them.
I then added two more columns: one to specify the time the customer made the purchase—whether it was noon, afternoon, etc. I named it "Time Type."
The second column specified the date the transaction occurred (Saturday, Sunday, Monday, etc.). I named it "Date Type."
I then added columns like "Day," "Month," and "Hour" for a more comprehensive analysis. Here's an explanation of the two notations I used. First code:
Date.DayOfWeekName(Date.From([date]))
1. [date]
This is the column in the table that contains the dates of each sale (for example, 2025-03-15).

2. Date.From([date])
This function ensures that the values ​​in this column are converted to a date type.
Sometimes, Power Query treats the column as text, so we convert it to a date so we can use it using date functions.

✅ Example:
If the value "2025-03-15" is text → after Date.From, it becomes #date(2025, 3, 15)

3. Date.DayOfWeekName(...)
This function returns the name of the day on which this date falls.
That is, if the date is 2025-03-15 → return "Saturday"

Coding 2:
Let
h = [custom],
Result =
If h >= 5 and h < 12, we write "morning"
Else if h >= 12 and h < 15, we write "noon"
Else if h >= 15 and h < 17, we write "afternoon"
Else if h >= 17 and h < 19, we write "sunset"
Else if h >= 19 and h < 24, we write "dinner"
Else "midnight"

Result
1. Let... in

This is the basic form of any code in M.

The part after let is where we write the operations or values ​​we want to define.

The part after in is the final result we will return.

2. h = [Custom]
Here, the value is stored in the [Custom] column in a variable named h.
This column typically contains the hour you extracted from the order time.
For example, if 10 AM → h = 10

3. Result = ...
Here, we create a series of if...else conditions to divide the day into time periods based on the hour value h.

I then used Pivot Tables and discovered that total sales amounted to approximately EGP 237,000 from over 7,500 sales. The most popular type of coffee was latte,
and sales were highest in January and March, as well as between 12 PM and 5 PM. Tuesday saw the highest traffic and revenue of the week, with 96% of customers paying in cash.
Only one machine was doing most of the work.

I compiled all of this analysis into a dashboard that displays every detail—from revenue and number of orders to coffee types and machine performance—in a simple and clear way.
