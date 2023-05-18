# gojsontoxml

conversion from `map[string]interface{}` a.k.a `any` to (hopefully) a valid xml in `[]byte`.

## usage example

```go
dataBytes, err := gojsontoxml.JsonToXml(data)

if err != nil {
	log.Panicln(err)
	return
}
  
w.Header().Set("Content-Type", "application/xml")
w.Write(dataBytes)
	
```

Todo: test cases 

Complains, feedbacks, opinions are appreciated.
