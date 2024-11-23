# Time-Analysis-Functions
See what opportunities come with time series analysis functions! 🚀
------------

Hi! In this post, I will show you the most important elements of time series analysis that will be useful for designing reports. Fasten your seatbelts... THE PLANE IS TAKING OFF 🚀🚀

Let’s start with YTD.

You can calculate the sales volume from the beginning of the year by modifying the date filter context to include dates starting from January 1st and ending with the month corresponding to the current cell being calculated.

CODE:

![image](https://github.com/user-attachments/assets/abd3b353-1897-431d-b8e2-8d32d9ed79c7)

Detailed explanation of the components:

CALCULATE
This is the most important function in DAX that changes the calculation context.
In this case, it modifies the context to include only dates from the beginning of the year to the selected date.

Sales[Sales Amount]

This is a column or measure containing sales values (e.g., transaction amounts).
CALCULATE will apply to these values.

DATESYTD('Date'[Date])

This function returns a set of dates from the start of the year (Year-To-Date) up to the currently filtered date in the report.
It works based on the date column from the calendar table ('Date'[Date]).

How does it work in practice?

For example, if you select March 15, 2024, in your report:

The DATESYTD function will select all dates from January 1, 2024, to March 15, 2024.
The CALCULATE function will filter the sales data only for these dates.
The result is the total sales from the beginning of the year to March 15, 2024.

Effect:

![image](https://github.com/user-attachments/assets/338689b6-fa0f-454f-93e6-73521d7929f2)

We can also use the TOTALYTD function, which will give the same effect as the measure above. Thanks to its name, it is easy to understand what it does, but it is still worth mastering the original syntax using CALCULATE, as it allows for more advanced calculations.

![image](https://github.com/user-attachments/assets/02c27452-105e-4964-bf16-514b96f90f1b)

![image](https://github.com/user-attachments/assets/5db14a51-d13f-43b9-a79e-924651269a9e)

TOTALYTD

It is a ready-made DAX function to calculate the cumulative value from the beginning of the year to a specific date.
It makes the work easier because you don't need to manually use CALCULATE and DATESYTD. The function does this automatically.

Similarly to year-to-date calculations, there are built-in functions for calculating from the beginning of the quarter or month: TOTALQTD, TOTALMTD. See below:

![image](https://github.com/user-attachments/assets/b8ba00aa-199a-40e1-b3a9-53bb1271bea8)

Let's now move on to CALCULATING VALUES FOR EARLIER PERIODS.

End users of the report often need to compare aggregated values for the same period of the previous year - PY.

The DAX language provides an advanced function to perform this task:

![image](https://github.com/user-attachments/assets/0bf018da-6332-4c28-be64-d3c205e1b206)

![image](https://github.com/user-attachments/assets/238c4cb4-b5e1-49dc-9966-fde67261a60a)

SAMEPERIODLASTYEAR returns a set of dates corresponding to the currently selected dates, shifted one step back.
It is a specialized version of the general DATEADD function. We can therefore define the same PY sales measure using the following code:

![image](https://github.com/user-attachments/assets/c3dc1f26-b9ab-45f3-b52e-dd1fab8daae3)

![image](https://github.com/user-attachments/assets/c7a0b6f2-d555-466e-920c-c1ac9ae00816)

In a similar way, you can calculate values for the previous quarter (PQ), month (PM), and day (PD).

![image](https://github.com/user-attachments/assets/7ece5e13-d940-416d-8a4d-a84bac910879)

Sometimes we want to find the total value of a measure for the previous year. PARALLELPERIOD helps with this, as it returns the full range specified by the third parameter, instead of the partial range returned by DATEADD.

![image](https://github.com/user-attachments/assets/ebdabf6b-dbd8-4862-b6ac-96cecac22e6b)

![image](https://github.com/user-attachments/assets/3d3712a7-7aef-4c34-bac6-51de9a5ee29c)

In a similar way, you can calculate the previous quarter (PQ), month (PM), and day (PD).

![image](https://github.com/user-attachments/assets/c6d09215-7408-420c-bece-4807dce808e3)

There are also functions similar to PARALLELPERIOD that are NOT IDENTICAL.
These include PREVIOUSYEAR, PREVIOUSQUARTER, etc., as well as NEXTYEAR, NEXTQUARTER, etc.

![image](https://github.com/user-attachments/assets/baecb1d9-ba82-4320-ab47-54b624d0f906)

The difference between them is visible in the above image.
The PARALLELPERIOD measure returns the value for December 2007, both for the whole year of 2008 and for the first quarter of 2008, while PREVIOUSMONTH always returns results for the same number of selected months.

The last point of this post will be CALCULATING DIFFERENCES COMPARED TO EARLIER PERIODS.
If you want your report to be considered the "real deal," you must know this! 📊✨

One must-have operation is finding the change between the current value of a measure and its value in the previous year. The change can be presented as a difference or a percentage result.

The difference between the current sales value and the result for the same period of the previous year is a simple subtraction. See below:

![image](https://github.com/user-attachments/assets/1992c280-595e-442f-b1b8-725c094c0a28)

![image](https://github.com/user-attachments/assets/fefc01a5-db01-4b39-bac3-27196b8212a7)

![image](https://github.com/user-attachments/assets/df8a5150-1a23-46b7-90d7-5d8dec8dfee2)

Now let's present the percentage change.

![image](https://github.com/user-attachments/assets/1ef2ab67-7c39-42a3-ade4-67faac9eb042)

![image](https://github.com/user-attachments/assets/bf56a7ab-ed30-49bb-9d01-2d324913292b)

I hope you survived this post. If so, a bright future awaits you :D ✨✨✨

As you can see, we are gradually raising our bar on data visualization ✨🚀 I hope you enjoyed it: )

That's all in this article !

I hope you will use this technique and show it off at work : )

Greetings, Mateusz Rajca



