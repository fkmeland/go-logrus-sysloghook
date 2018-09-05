# Syslog Hooks for Logrus <img src="http://i.imgur.com/hTeVwmJ.png" width="40" height="40" alt=":walrus:" class="emoji" title=":walrus:"/>
## Forked from github.com/sirupsen/logrus, just added a formatting option

### Usage

```go
import (
  "log/syslog"
  "github.com/sirupsen/logrus"
  "github.com/fkmeland/go-logrus-sysloghook"
)

func main() {
  log       := logrus.New()
  hook, err := sysloghook.NewSyslogHook("udp", "localhost:514", syslog.LOG_INFO, "", nil)

  if err == nil {
    log.Hooks.Add(hook)
  }
}
```

If you want to connect to local syslog (Ex. "/dev/log" or "/var/run/syslog" or "/var/run/log"). Just assign empty string to the first two parameters of `NewSyslogHook`. It should look like the following.

```go
import (
  "log/syslog"
  "github.com/sirupsen/logrus"
  "github.com/fkmeland/go-logrus-sysloghook"
)

func main() {
  log       := logrus.New()
  hook, err := sysloghook.NewSyslogHook("", "", syslog.LOG_INFO, "", nil)

  if err == nil {
    log.Hooks.Add(hook)
  }
}
```
