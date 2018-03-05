


podfile contents

```ruby
use_frameworks!

do 'xxxProject' target
  pod 'Alamofire'
end 
```

how to use Alamofire request

```swift
func step1(){
    Alamofire.request("https://httpbin.org/get", method: .get).responseJSON { response in
        let result = response.result
        print(result)
    }
    
}
func step2(){
    
    let baseUrl = "https://httpbin.org/get"
    let parameters = ["foo":"bar","girs":"aepoge"]
    
    Alamofire.request(baseUrl,
                      method: .get,
                      parameters: parameters,
                      encoding: URLEncoding(destination: .queryString),
                      headers: nil)
        .responseJSON { response in
            let result = response.result
            print(response)
    }
    
}
```
