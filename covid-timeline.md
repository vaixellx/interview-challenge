# Covid Timeline
Create a web application using Typescript, NodeJS (NestJS would be a plus), and React (NextJS would be a plus) to generate COVID Patient Timeline (see [design](#design))

## Requirement
- User can click on (+) to add new patient up to 8 patients.
- User can add each patient information using form on top, the patient contains these data
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
- User can remove patient and timeline entries by click on Remove Patient button on he top right.
- Make it responsive and look nice on all screen sizes.

- **BONUS POINT I:** Cover the use case with test.
- **BONUS POINT II:** Feel free to make it better than the given design 😉
- **BONUS POINT III:** Use GraphQL as API

## Design
![localhost_3000_ (1)](https://user-images.githubusercontent.com/1606989/138546503-b4035c95-c730-4104-ad86-68134614e937.png)


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
