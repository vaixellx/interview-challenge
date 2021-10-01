# Need to combined with possible contact feature

# House Timeline Extended
There are 4 strangers living in the same house: **Bill, Elon, Mark, and Tim**. This house has 3 shared areas where they can live together: **Living Room, Kitchen, and Backyard**.

Due to COVID-19 situation they decided to track and keep house areas on the website to make it easier to see how often they’re facing each other.

The rules of this house are that each area gate will open for in/out only at 00 and 30 each hour, for example 00:00, 00:30, 15:30, etc.

## Requirement
- Create a web application using NodeJS (NestJS) and React (NextJS) to store the records of areas usage (see [design](#design))
- Record will contain person name,room, and time period
- **Name** input is a dropdown containing `Bill, Elon, Mark, Tim` as values.,
- **Room** input is a dropdown containing `Living Room, Kitchen, Backyard` as values.
- **From** and **To** are dropdowns containing `00:00, 00:30, 01:00, …, 23:30`
- Add form validation to ensure that each person can live at only 1 place at the same time
- Add a timeline calendar containing people and timeslot
- Draw record as a bar with color on timeline calendar. Color of each bar is depending on the area they’re living on
  - Living room => Blue
  - Kitchen => Yellow
  - Backyard => Green
- Store data in database as you desire.
- **BONUS POINT I:** Cover the use case with test.
- **BONUS POINT II:** Feel free to make it better than the given design 😉
- **BONUS POINT II:** Use GraphQL

## Design

Empty state
![localhost_3000_ (1)](https://user-images.githubusercontent.com/1606989/134034250-160bdd0b-8455-4900-9eae-89a723877212.png)


Filled state
![localhost_3000_ (2)](https://user-images.githubusercontent.com/1606989/134034296-d734d856-7a6f-4b1a-8655-3ae66054f112.png)


## Style Guideline
Font: [Roboto Slab](https://fonts.google.com/specimen/Roboto+Slab)
#### Color Codes
```
background: #f5f5f5;
font-color: #555555;
blue: #5882E3;
black: #343a40;
gray: #ced4da;
living-room: #17a2b8;
backyard: #28a745;
kitchen: #ffc107;
```
