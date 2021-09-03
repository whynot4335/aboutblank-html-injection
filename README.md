# about:blank HTML injection
PoC for the about:blank html injection phishing technique

This technique uses `window.open('about:blank', ...)` in combination with `document.write('<iframe ...>')` and `document.title = 'Something'` to create a new about:blank window which can be disguised as a login page with the correct title. This technique was discovered in the wild as a "Discord Nitro Gift" by making people log in with their steam account.

## PoC Screenshot [Browser: Google Chrome Dev Channel]
![Image of Proof of Concept](https://cdn.discordapp.com/attachments/797439482126139392/883336418947113040/unknown.png)

## Versions

Tested against the following browsers (All tested on Manjaro Linux x64 using latest AUR versions, except for the Android browsers)

| Browser name             	| Browser version                                                  	| PoC worked 	|
|--------------------------	|------------------------------------------------------------------	|------------	|
| Brave                    	| 1.28.106                                                         	| ✅          	|
| Firefox                  	| 91.0.2 (64-bit)                                                  	| ❌          	|
| Chromium                 	| 92.0.4515.159 (Official Build)                                   	| ✅          	|
| Google Chrome            	| 93.0.4577.63 (Official Build) + 95.0.4628.3 (Official Build) dev 	| ✅          	|
| Opera                    	| 78.0.4093.184-1 (x86_64)                                         	| ✅          	|
| Brave Android            	| 1.28.106, Chromium 92.0.4515.159                                 	| ✅          	|
| Chrome Android           	| 92.0.4515.159                                                    	| ✅          	|
| Samsung Internet Android 	| 15.0.2.47                                                        	| ❌          	|
| Microsoft Edge           	| 93.0.961.38 (Official Build)                                     	| ✅          	|

### Posible fixes
Block JavaScript from modifying html when opening a window on about:blank (just like when JavaScript tries to change data cross-domain) or have the browser not display about:blank as url, but the original domain name (this last mitigation was seen on both Firefox and Samsung Internet Android)

### Conclusion
It seems like this is an issue on Chromium-based browsers only. This technique can be used to have a greater chance of success on phishing attacks, as the "hostname" (about:blank) is not immediately deemed suspicious by everyone.
