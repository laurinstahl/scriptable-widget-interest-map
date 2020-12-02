# scriptable-widget-interest-map

![A medium-sized widget view of Boston Common.](media/3DFC39F6-962E-4255-9337-DBAD908AAAC6.jpeg?raw=true)  |  ![A medium-sized widget view of Spot Pond.](media/C9BF6F28-93CC-4F8F-A848-58FD1CDB901B.png?raw=true)
| --- | --- |

## Performance Metrics
Performance metrics are stored in a CSV file and can be read easily using the "Charty" app with this shortcut:

https://www.icloud.com/shortcuts/932366757e124075ae6f755da89563eb

|  Performance Graph   |   Investigation  |
| --- | --- |
| ![A graph depicting getCurrentLocation taking much longer than the other APIs](media/BB6E2934-E843-4F2F-9668-3C4890FA22DD.png?raw=true "getCurrentLocation Latency with 10 meter accuracy") | In this graph we noticed that getCurrentLocation with 10 meter accuracy would occasionally take a long time to execute. This was surprising because other apps seem to get the current location quickly and the latency is inconsistent. |
| ![A graph depicting getCurrentLocation taking less time consistently after being set to 100 meters. The other APIs have a blip with higher latency but that's believed to be related to internet access.](media/94455C7B-176B-4DA3-8754-A4CDC5AB482A.png?raw=true "getCurrentLocation Latency with 100 meter accuracy in the second half") | We modified getCurrentLocation to use 100 meter accuracy and not only did it's latency drop considerably but it stayed consistent. What's interesting is now the other APIs spiked. It's unlikely that both Wikipedia and Google Maps had issues at the same time so we believe the latency spikes were caused by a bug or an issue local to the phone running the script. Our current theory is that the widget was run from inside a car that was trying to connect to a house's wifi causing a bad internet connection. |
| ![A graph depicting all APIs with normal latency.](media/B6B02EBA-BCE4-45BC-A7B1-15C5B5363CBF.png?raw=true "APIs are back to normal latency") | After additional testing the spikes have not occurred again. Everything looks normal! |
