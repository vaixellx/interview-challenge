# Covid Timeline
Create a web application using Typescript, NodeJS (NestJS would be a plus), and React (NextJS would be a plus) to generate COVID Patient Timeline (see [design](#design))

## Requirement
- User can add patient information using form on top, the patient contains these data
  - Gender: string
  - Age: integer
  - Occupation: string
- User can add timeline entry using form on the right, a timeline entry contains these data
  - Time From: datetime
  - Time To: datetime
  - Detail: string
  - Location Type: string
  - Location: string
- Location type can be only these following value
  - INDOOR
  - OUTDOOR
  - HOME
  - TRAVELLING
- When location type is `INDOOR` and `OUTDOOR` user need to specify the location name.
- On the left side use patient data and timeline entry data to display data as show in the design
  - Timeline activities must be sorted by Time.
  - Each timeline entry must not collapsed with other entry.
  - Timeline activities must be grouped by date.
  - Visited locations must be sorted by name.
  - User can remove timeline entry when click on (x) button.
- Make it responsive and look nice on all screen sizes.
- **Update README.md to containing setup instructions, pretend that reviewer who has brand new laptop can set it up successfully.**

- **BONUS POINT I:** Cover the use case with test.
- **BONUS POINT II:** Feel free to make it better than the given design 😉
- **BONUS POINT III:** Use GraphQL as API

## Design
![covid-timeline](https://user-images.githubusercontent.com/1606989/143536325-c226bc8d-6e80-4a01-a335-77a6d493d9bc.png)


## Style Guideline
Font: [Roboto Slab](https://fonts.google.com/specimen/Roboto+Slab)
#### Color Codes
```
--background: #012d5e;
--font-color: #ffffff;
--blue: #5882E3;
--light-blue: #254870;
--yellow: #ffc107;
--red: #dc3545;
--white: #fff;
```
