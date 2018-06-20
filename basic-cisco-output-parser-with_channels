package main

import (
  "fmt"
  "time"
  "strings"
)

func main()  {
  ch := make(chan string, 2)
  go write(ch)
  for v := range ch {
    //fmt.Printf("%s has been read\n", v)
    go parser(v)
    //fmt.Printf("Length of channel %d after reading \n", len(ch))
    time.Sleep(2 * time.Second)
  }
}

func write(ch chan string) {
  output := `Switch Uptime                   : 34 weeks, 3 days, 10 hours, 18 minutes
Base ethernet MAC Address       : 00:10:AA:AA:AA:00
Motherboard assembly number     : 73-0000-00
Power supply part number        : 000-0000-01
Motherboard serial number       : AAAAAAAAUAA
Power supply serial number      : BBCCDDEEFFF
Model revision number           : CC
Motherboard revision number     : AA
Model number                    : WS-C3750G-48TS-S
System serial number            : BBCCDDEEFFF
SFP Module assembly part number : 11-2345-67
SFP Module revision number      : AA
SFP Module serial number        : CATBBCCDD2
Top assembly part number        : 000-12345-67
Top assembly revision number    : BB
Version ID                      : V01
CLEI Code Number                : AABBCCDD`
  show_string := strings.Split(output, "\n")
  for _,each_string := range show_string {
    ch <- each_string
    fmt.Printf("%s has been written\n\n", each_string)
    //fmt.Printf("Length of channel %d\n", len(ch))
  }
  close(ch)
}

func parser(v string) {
    sec_string := strings.Split(v, ": ")[1]
    fmt.Printf("%s \n", sec_string)
}
