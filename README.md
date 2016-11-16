# HTTP/2 on cloudfornt

On September 2016 Amazon AWS [announced](https://aws.amazon.com/about-aws/whats-new/2016/09/amazon-cloudfront-now-supports-http2/) HTTP/2 support on cloudfront CDN.

HTTP/2 is a major revision of the HTTP protocol. This new version has several features that make page loading and rendering faster:

- **Single Connection**: Only one connection to the server is used to load a website, and that connection remains open as long as the website is open. This reduces the number of round-trips needed to set up multiple TCP connections
  
- **Multiplexing**: Multiple requests are allowed at the same time, on the same connection. Previously, with HTTP/1.1, each transfer would have to wait for other transfers to complete. 

- **Header compression**: reduces the overhead bytes downloaded by the client, helping get the content to the viewer sooner

HTTP/2 is backwards-compatible with HTTP/1.1 - so any [non-supported browser](http://caniuse.com/#feat=http2) will keep working as today.

HTTP/2 is enabled by default for all new Amazon CloudFront distributions, and for existing distributions HTTP/2 can be enabled by editing the distribution configuration.

![edit distribution configuration](http://rawdata.adicarmel.com.s3.amazonaws.com/tmp/http2.png)

To test the effectiveness of HTTP\2 - i created small web page that download multiple images from cloudfront distributions and paint them on canvas.

I measured the time it take to download and paint those images from HTTP/1.1 cloudfront distribution and then from HTTP/2 cloudfront distribution.

The results are great - especially on mobile - we can see that it reduced the download time significantly, without any changes on our code.

You can check it yourself by running this [test page](https://dm1fjyvtm5scl.cloudfront.net/http2/index.html) I created, and see the difference between HTTP/1.1 and HTTP/2

![test results](http://rawdata.adicarmel.com.s3.amazonaws.com/tmp/http2-res.png)

I highly recommend to give it a try and test your website/product performance with HTTP/2.








