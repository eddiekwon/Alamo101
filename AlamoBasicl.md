


podfile setup

```ruby
use_frameworks!

target 'xxxProjectName' do
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

if header info needed.

```swift

func step4WithHeader_usingResponseString(){
    
    // 1 HEADER INFO
    let authStr = "73816de3-8ae3-31c1-bcfa-80b58eb82df4"
    
    let headers  = [ "Authorization": "Bearer \(authStr)"]  
    
    // 2 BASE URL
    let baseUrl = "https://xxxxxx.xxxx.xxx/21" //important: Do not append a slash at the end of string
 
    let parameters = ["":""]
    
    Alamofire.request(baseUrl,
                      method: .get,
                      parameters: parameters,
                      encoding: URLEncoding(destination: .queryString),
                      headers: headers)
        .validate(contentType: ["application/json"])
        
        .responseString { (response ) in  //important!!! per sever
            
            print("👧🏻val is \n👧🏻\n")
            switch response.result {
            case .success(let value):
                //print("response headerfields \(response.request?.allHTTPHeaderFields)")
                print("\(value)")
                //completionHandler(value as? NSDictionary, nil)
            case .failure(let error):
                print("signin_post error: ", error)
                //completionHandler(nil, error)
            }
            
        }
    
}
```
