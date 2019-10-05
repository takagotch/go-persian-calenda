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



func TestRMonthDay(t *testing.T) {

}

func TestFirstLast(t *testing.T) {
  ti := Date(1394, Mehr, 2, 12, 59, 59, 0, Iran())
  
  if ti.FirstMonthDay().Weekday() != Charshanbeh {
    t.Error(
    
    )
  }
  
  
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


