# Practice_URLScheme
>APP A open APP B

### 主要使用下列方法(APP A)：
```
            if let url = URL(string: decodedURL) {
                if UIApplication.shared.canOpenURL(url) {
                    UIApplication.shared.open(url, options: [:], completionHandler: nil)
                }
            }
          
```
### APP B Info.plist:
-  Add -> URL Types -> URL identifier -> com.dcview.TextReader(APP Bundle ID)
-  Add -> URL Types -> URL Schemes -> textreader
```
<key>CFBundleURLTypes</key>
	<array>
		<dict>
			<key>CFBundleURLSchemes</key>
			<array>
				<string>textreader</string>
			</array>
			<key>CFBundleURLName</key>
			<string>com.dcview.TextReader</string>
		</dict>
	</array>
```
### APP B AppDelegate:
show text
```
func application(_ app: UIApplication, open url: URL, options: [UIApplicationOpenURLOptionsKey : Any] = [:]) -> Bool {
        let message = url.host?.removingPercentEncoding
        let alertController = UIAlertController(title: "Incoming Message", message: message, preferredStyle: .alert)
        let okAction = UIAlertAction(title: "OK", style: UIAlertActionStyle.default, handler: nil)
        alertController.addAction(okAction)
        window?.rootViewController?.present(alertController, animated: true, completion: nil)
        
        return true
    }
```
### APP A Info.plist:
```
<key>LSApplicationQueriesSchemes</key>
    <array>
        <string>textreader</string>
        <string>fb</string>
        <string>whatsapp</string>
    </array>
```


