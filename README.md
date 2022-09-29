# fluent-translator

Scala non-blocking library for working with Microsoft, Google etc. language translation services via a fancy DSL.

Examples
--------------
Using Microsoft translator client:
```scala
import com.smartelk.fluent.translator.Dsl._

implicit object client extends MicrosoftTranslatorClient {
  val clientId = "microsoft client id"
  val clientSecret = "microsoft client secret"
}

Microsoft give me a translation of "Comment vas-tu?" to "en" as future //Future[String]
Microsoft give me a translation of "What a lovely weather today!" from "en" to "fr" withContentType `text/html` as future //Future[String]
Microsoft give me many translations of "Doing well by doing good" from "en" to "ru" as future //Future[GetTranslationsResponse]
Microsoft give me translations(3) of "Paris holidays" from "en" to "ru" withCategory "general" as future //Future[GetTranslationsResponse]
Microsoft speak "I'm doing well enough now" in "en" withAudioContentType `audio/mp3` as future //Future[SpeakResponse]
Microsoft speak "How are you doing?" in "en" withQuality MinSize as future //Future[SpeakResponse]
```

Using Google translator client:
```scala
import com.smartelk.fluent.translator.Dsl._

implicit object client extends GoogleTranslatorClient {
  val apiKey = "google api key"
}

Google give me a translation of "Comment vas-tu?" to "en" as future //Future[String]
Google give me a translation of "What a lovely weather today!" from "en" to "fr" withContentType `text/html` as future //Future[String]
```

Installation
--------------
Build.sbt:
```scala
resolvers += Resolver.bintrayRepo("smartelk", "maven")
libraryDependencies += "com.smartelk" %% "fluent-translator" % "2.1.0"
```

Dependencies
--------------
Library uses as few dependencies as possible, though it depends directly on few awesome projects:  
*akka* & *dispatch* (scala wrapper *for async-http-client*) - to help make things working in a non-blocking way;  
*json4s* - to help with json processing; 

Useful links
--------------
#### Microsoft
Registering application at Microsoft and obtaining client id and client secret:  
https://datamarket.azure.com/developer/applications/

List of supported language codes by Microsoft translator:  
https://msdn.microsoft.com/en-us/library/hh456380.aspx

#### Google
Creating project at Google and obtaining api key:  
https://console.cloud.google.com/projectselector/apis/credentials

List of supported language codes by Google translator:  
https://cloud.google.com/translate/v2/using_rest
