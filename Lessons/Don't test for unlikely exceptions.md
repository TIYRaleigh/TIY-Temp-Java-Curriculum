
In Java there are many classes which declare that they can throw exceptions. For example you could potentially receive an IOException when reading a file from disk, though it's quite unlikely. This isn't a behavior you are intentionally adding to your class. Heck, it's probably quite difficult to cause this exception to be triggered. So, why bother testing for it? 

Instead, just tack a throws statement onto your test method's signature and let the JUnit handle the Exception. If JUnit receives an uncaught exception it will simply report an error, which still communicates that your test failed.
