# Clock Maker +2

นาฬิกา analog แบบเข็มรุ่นล่าสุดนอกจากจะสามารถบอกเวลาเป็นวินาทีแล้วเข็มแต่ละเข็มยังเดินแบบเรียบเพื่อลดเสียงรบกวนอีกด้วย โดยเข็มแต่ละเข็มจะทำการขยับเล็กน้อยในทุกๆ มิลลิวินาทีโดย 1 วินาทีจะประกอบไปด้วย 1000 มิลลิวินาทีจงเขียนฟังก์ชันเพื่อรับคำนวนองศาของเข็มสั้น, เข็มยาว และเข็มวินาที ณ เวลาที่ถูกอินพุตเข้าไปโดยแสดงองศาของแต่ละเข็มเป็นทศนิยม 5 ตำแหน่ง

## Test Cases

```ruby
30 / 3600
clock_arms_radius("09:00:30.500")
> [270.25416, 3.055, 183]

clock_arms_radius("09:30:45.700")
> [285.38083, 184.57, 274.2]

clock_arms_radius("12:10:10.200")
> [5.08466, 61.02, 61.2]

clock_arms_radius("20:41:52.292")
> [260.93543, 251.2292, 313.752]
```

---

[< Prev](https://vaixellx.github.io/interview-challenge/clock-maker/th/additional-1)
