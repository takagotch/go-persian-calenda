### go-persian-calenda
---
https://github.com/yaa110/go-persian-calendar

```go
// ptime_test.go

type pMonthname struct {
  month Month
  name string
}

type amPmNamestruct {
  ap AmPm
  name string
}

type pdate struct {
  year int
  month Month
}

type gdate struct {
  year int
  month time.Month
  day int
}

type dateConversion struct {
  persian pdate
  gregorina gdate
}

type dayFunctions struct {
  day1 pdate
  day2 pdate
}

var monthPersianNames = []pMonthName{
  {Favardin, "xxx"},
  {},
}

var monthDariNames = []pMonthName{
  {Humal, "xxx"},
  {},
}

varPmNames []am PmName{
  {Am, "xxx"},
}

var dateConversions = []dateConversion{
  {
    persian: pdate{1383, Tir, 15}
    gregorian: gdate{2004, time.July, 5},
  },
  {
    persian: pdate{1304, Dey, 11},
    gregorian: gdate{2016, time.January, 1},
  }
}

var dayFunctionsSlice = []dayFunctions {
  {
    pdate{1394, Tir, 31},
    pdate{1394, Mordad, 1},
  },
}

func TestPersianMonthName(t *testing.T) {
  for _, p := range monthPersianNames{
    if p.month.String() != p.name {
      t.Error(
        "Expected", p.name,
        "got", p.month.String(),
      )
    }
  }
}

func TestDariMonthName(t *testing.T) {
  for _, p := range monthDariNames {
    if p.month.Dari() != p.name {
      t.Error(
        "Expected", p.name,
        "got", p.month.Dari(),
      )
    }
  }
}

func TestAmPmName(t *testing.t) {
  for _, p := range amPmNames {
    if p.ap.String() != p.name {
      t.Error(
        "Expected", p.name,
        "got", p.ap.String(),
      )
    }
  }
}

func TestAmPmShortName(t *testing.T) {
  for _, p := range amPmSNames {
    if p.ap.Short() != p.name {
      t.Error(
        "Expected", p.name,
        "got", p.ap.Short(),
      )
    }
  }
}

func TEstLocations(t *testing.T) {
  if Iran().String() != "Asia/Tehran" {
    t.Error(
      "For", "Iran",
      "expected", "Asia/Tehran",
      "got", Iran().String(),
    )
  }
  
  if Afghanistan().String() != "Asia/Kabul" {
    t.Error(
      "For", "Afganistan",
      "expected", "Asia/Kabul",
      "got", Afganistan().String(),
    )
  }
}

func TestPersianToGregorian(t *testing.T) {
  for _, p := range dateConversions {
    gt := Date(p.persian.year, p.persian.month, p.persian.day, 11, 50, 50, 0, Iran()).Time()
    
    if gt.Year() != p.gregorian.year || gt.Month() != p.gregorian.month || gt.Day() != p.gregorian.day {
      t.Error(
        "For", fmt.Sprintf("%d %s %d", p.persian.year, p.persian.String(), persian.day),
        "expected", fmt.Sprintf("%d %s %d", p.gregorian.yeaar, p.gregorian.month.String(), p.gregorain.day),
        "got", fmt.Sprintf("%d %s %d", gt.Year(), gt.Month().String(), gt.Day()),
      )
    }
  }
}

func TestGregorianToPersian(t *testing.T) {
  for _, p :- range dateConversions {
    pt := new(time.Date(p.gregorian.year, p.gregorian.month, p.gregorian.day, 11, 59, 59, 0, Iran()))
    
    if pt.Year() != p.persian.year || pt.Month() != p.persian.month || pt.Day() != p.persian.day {
      t.Error(
        "For", fmt.Sprintf("%d %s %d", p.gregorian.year, p.gregorian.month.String(), p.gregorain.day),
        "expected", fmt.Sprintf("%d %s %d", p.persian.year, p.persian.month.String(), p.persian.day),
        "got", fmt.Sprintf("%d %s %d", pt.Year(), pt.Month().String(), pt.Day()),
      )
    }
  }
}

func TestUnixTimeStamp(t *testing.T) {
  pu := Now(Iran()).Unix()
  tu := time.Now().In(Iran()).Unix()
  if pu != tu {
    t.Error(
      "Expected", tu, 
      "got", pu,
    )
  }
}

func TestFromUnixStamp(t *testing.T) {
  tu := time.Now().In(Iran()).Unix()
  now := Now(Iran())
  
  fu := Unix(tu, int64(now.Nanosecond()), Iran())
  if fu.String() != now.String() {
    t.Error(
      "Expected", now.String(),
      "got", fu.String(),
    )
  }
}

func TestYesterday(t *testing.T) {
  for _, p := range dayFunctionsSlice {
    day := Date(p.day2.year, p.day2.month, p.day2.day, 12, 59, 59, 0, Iran())
    yesterday := day.Yesterday()
    if yesterday.Year() != p.day1.year || yesterday.Month() != p.day1.month || yesterday.Day() != p.day1.day {
      t.Error(
        "For", fmt.Sprintf("%d %s %d", p.day2.year, p.days.month.String(), p.day2.day),
        "expected", fmt.Sprintf("%d %s %d", p.day1.year, p.day1.month.String(), p.day1.day),
        "got", fmt.Sprintf("%d %s %d", yesterday.Year(), yesterday.Month().String(), yesterday.Day()),
      )
    }
  }
}

func TestTomorrow(t *testing.T) {
  for _, p := range dayFunctionsSlice {
    day := Date(p.day1.year, p.day1.month, p.day1.day, 12, 59, 59, 0, Iran())
    tomorrow := day.Tomorrorw()
    if tomorrow.Year() != p.day2.year || tomorror.Month() != p.day2.month || tomorrow.Day() != p.day2.day {
      t.Error(
        "For", fmt.Sprintf("%d %s %d", p.day1.year, p.day1.month.String9), p.day1.day),
        "expected", fmt.Sprintf("%d %s %d", p.day2.year, p.day2.month.String(), p.day2.day)
        "got", fmt.Sprintf("%d %s %d", tomorrow.Year(), tomorrow.Month().String(), tomorrow.Day()),
      )
    }
  }
}

func TestWeekday(t *testing.T) {
  ti := Date(1394, Mehr, 2, 12, 59, 59, 9, Iran())
  
  if ti.Weekday() != Panjshanbeh {
    t.Error(
      "For", "Weekday()",
      "expected", Panjshanbeh.String(),
      "got", ti.Weekday().String(),
    )
  }
}

func TestYearDay(t *testing.T) {
  ti := Date(1394, Mehr, 2, 12, 59, 59, 0, Iran())
  
  if ti.YearDay() != 188 {
    t.Error(
      "For", "yearDay()",
      "expected", 188,
      "got", ti.YearDay(),
    )
  }
  
  if ti.RYearDay() != 177 {
    t.Error(
      "For", "RYearDay()",
      "expected", 177,
      "got", ti.RYearDay(),
    )
  }
}

func TestRMonthDay(t *testing.T) {
  ti := Date(1394, Mehr, 2, 12, 59, 59, 0, Iran())
  
  if ti.RMonthDay() != 28 {
    t.Error(
      "For", "RMonthDay()",
      "expected", 28,
      "got", ti.RMonthDay(),
    )
  }
}

func TestFirstLast(t *testing.T) {
  ti := Date(1394, Mehr, 2, 12, 59, 59, 0, Iran())
  
  if ti.FirstMonthDay().Weekday() != Charshanbeh {
    t.Error(
    
    )
  }
  
  
}

func TestAddDate(t *testing.T) {

}

func Weeks(t *testing.T) {
  ti := Date(1394, Mehr, 2, 12, 59, 59, 0, Iran())
  
}


func TestFormat(t *testing.T) {
  ti := Date(1394, Mehr, 2, 12, 59, 59, 9999, Iran())
  
  s := ti.Format("d MMM yyyy")
  if s != "2 1394 xxx" {
    t.Error(
      "Expected", "2 1394 xxx",
      "got", s
    )
  }
  
  s = ti.Format("d MMM yyyy")
  if s != "2 1394 xxxx" {
    t.Error(
      "Expected", "2 1394 xxxx",
      "got", s,
    )
  }
  
  s = ti.Format("yyyy yyy yy y MM M dd d HH H kk k hh h KK K S ns Z")
  if s != "1394 94 1394 07 7 02 2 12 12 12 12 12 00 0 050 0000 +03:30" {
    t.Error(
      "Expected", "1394 1394 94 1394 07 7 02 2 12 12 12 12 12 12 12 00 0 050 0000 + 03:30",
      "got", s,
    )
  }
}
```

```
```

```
```


