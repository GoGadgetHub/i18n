# i18n




## import
```go
import "github.com/jingyuexing/i18n"
```


## usage

```go
package main

import (
	"fmt"

	i18n "github.com/jingyuexing/i18n"
)

func main(){
	messages := map[string]any{
        "en": i18n.Message{
            "greeting": i18n.Message{
                "welcome": "Welcome!",
            },
            "chat":i18n.Message{
                "button":"send",
            },
            "hint":i18n.Message{
            	"message":"the {name} is an user"
            }
        },
        "zh": i18n.Message{
            "greeting": i18n.Message{
                "welcome": "你好!",
            },
            "hint":i18n.Message{
            	"message":"the {name} is an user"
            }
        },
    }

	i18n := i18n.CreateI18n(&i18n.I18n{
	    Message:        messages,
	    // default language
	    Local:          "zh",
	    // When the key value specified in the Local language is not found,
	    // it will search again in the language specified by FallbackLocale.
	    // If it is also not found, the key passed in will be returned as is.
	    FallbackLocale: "en",
	})

	fmt.Printf("%s\n",i18n.T("greeting.welcome")) // will print "你好!"
	fmt.Printf("%s\n",i18n.T("hint.message"),map[string]any{
		"name":"Alan"
	}) // will print "the Alan is an user"
}
```
