# Possible Contact

Due to COVID-19 situation, let's say you are an event organizer and hold an event. After the event ended you just realized that one of our attendees has COVID-19 , So now you need to find out which person has possibly contacted the patient. The data we have is an access log for each attendance containing attendance name, operation (enter, exit), area they are entering or exiting, and timestamp

Criteria for detecting who is in the possibly contacted list is they are staying in the same area of patient at the same time.

For example we have this data in our database


|Attendee|Area|Operation|Time|
|--|--|--|--|
|Mark|VIP Zone|enter|09:00|
|Bill|Front Stage|enter|10:00 |
|Mark|VIP Zone|exit|10:30|
|Elon|Front Stage|enter|11:00|
|Tim|VIP Zone|enter|11:00|
|Bill|Front Stage|exit|12:00|
|Bill|VIP Zone|enter|12:30|
|Tim |VIP Zone|exit|13:00|
|Elon|Front Stage|exit|15:00|
|Mark|Front Stage|enter|15:30|
|Bill|VIP Zone|exit|16:00|
|Mark|Front Stage|exit|16:30|

Then when **Bill** is infected. The list of possible contracted contains **Elon** and **Tim** because
- **Elon** stayed at "Front Stage" together with Bill between 11:00 - 12:00
- **Tim** stayed at "VIP Stage" together with Bill between 12:30 - 13:00.

## Requirements
- Please create function named `possibleContactFinder`
- This function requires 2 arguments:
- First argument is an array of a restaurant branch's objects containing attendee name, area and operation (enter, exit) and time (`HH::MM` format), example:
  ```js
  [
    { name: "Mark", area: "VIP ZONE", operation: "enter", time: "09:00" },
    { name: "Bill", area: "Front Stage", operation: "enter", time: "10:00" },
    ...
  ]
  ```
- Second argument is name of attendee who is infected, example:
  ```js
  "Bill"
  ```
- This function will find and return possible contact list as an array containing
attendee name ordered alphabetically, example:
  ```js
  ["Elon", "Tim"]
  ```


## Test Cases
```js
accessLogs = [
  { name: "Mark", area: "VIP Zone",    operation: "enter", time: "09:00" },
  { name: "Bill", area: "Front Stage", operation: "enter|", time: "0:00 " },
  { name: "Mark", area: "VIP Zone",    operation: "exit", time: "10:30" },
  { name: "Elon", area: "Front Stage", operation: "enter", time: "11:00" },
  { name: "Tim",  area: "VIP Zone",    operation: "enter", time: "11:00" },
  { name: "Bill", area: "Front Stage", operation: "exit", time: "12:00" },
  { name: "Bill", area: "VIP Zone",    operation: "enter", time: "12:30" },
  { name: "Tim ", area: "VIP Zone",    operation: "exit", time: "13:00" },
  { name: "Elon", area: "Front Stage", operation: "exit", time: "15:00" },
  { name: "Mark", area: "Front Stage", operation: "enter", time: "15:30" },
  { name: "Bill", area: "VIP Zone",    operation: "exit", time: "16:00" },
  { name: "Mark", area: "Front Stage", operation: "exit", time: "16:30" }
]

possibleContactFinder(accessLogs, "Bill")
// => ["Elon", "Tim"]

possibleContactFinder(accessLogs, "Tim")
// => ["Bill"]

possibleContactFinder(accessLogs, "Mark")
// => []

possibleContactFinder(accessLogs, "Elon")
// => ["Bill"]
```
