---
title: "Fehlercodes für Windows-Runtime-Apps mit JavaScript | Microsoft-Dokumentation"
ms.custom: 
ms.date: 05/10/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology:
- javascript
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- JavaScript, Windows Runtime error codes
- VS.WebClient.Help.APPHOST9601
- VS.WebClient.Help.APPHOST9602
- VS.WebClient.Help.APPHOST9603
- VS.WebClient.Help.APPHOST9604
- VS.WebClient.Help.APPHOST9605
- VS.WebClient.Help.APPHOST9606
- VS.WebClient.Help.APPHOST9607
- VS.WebClient.Help.APPHOST9608
- VS.WebClient.Help.APPHOST9610
- VS.WebClient.Help.APPHOST9611
- VS.WebClient.Help.APPHOST9613
- VS.WebClient.Help.APPHOST9614
- VS.WebClient.Help.APPHOST9615
- VS.WebClient.Help.APPHOST9616
- VS.WebClient.Help.APPHOST9617
- VS.WebClient.Help.APPHOST9618
- VS.WebClient.Help.APPHOST9619
- VS.WebClient.Help.APPHOST9620
- VS.WebClient.Help.APPHOST9623
- VS.WebClient.Help.APPHOST9624
- VS.WebClient.Help.APPHOST9626
ms.assetid: 4c6d4e90-602a-4b56-ae74-3458929da442
caps.latest.revision: 1
author: erikadoyle
ms.author: edoyle
manager: jken
ms.translationtype: HT
ms.sourcegitcommit: 47057e9611b824c17077b9127f8d2f8b192d6eb8
ms.openlocfilehash: 89b91a3246d0a6e2980459c2c35c7361168bccd4
ms.contentlocale: de-de
ms.lasthandoff: 08/11/2017

---
# <a name="error-codes-for-windows-runtime-apps-using-javascript"></a>Fehlercodes für Windows-Runtime-Apps mit JavaScript
Hier sind die Fehlercodes aufgelistet, die von der Microsoft Visual Studio-Konsole angezeigt werden, wenn Windows-Runtime-Apps mit JavaScript entwickelt werden.
  
Fehler | Hinweise
----- | -------
APPHOST9601: „Can't load *remoteURI*. An app can't load remote web content in the local context.“ („remoteURI“ konnte nicht geladen werden. Eine App kann Remotewebinhalte nicht im lokalen Kontext laden.) | Weitere Informationen darüber, was im Webkontext zulässig ist, finden Sie unter [Features und Einschränkungen nach Kontext](https://msdn.microsoft.com/en-us/library/windows/apps/xaml/hh465373.aspx).
APPHOST9602: „'javascript:' is an invalid attribute value and will be ignored. Don't use 'javascript:' URIs in the local context.“ („javascript:“ ist ein ungültiger Attributwert und wird nicht beachtet. Verwenden Sie keine URIs mit „javascript:“ im lokalen Kontext.) | Aus Sicherheitsgründen können Sie keine URIs mit „javascript:“ im lokalen Kontext verwenden. Weitere Informationen darüber, was im lokalen Kontext zulässig ist, finden Sie unter [Features und Einschränkungen nach Kontext](https://msdn.microsoft.com/en-us/library/windows/apps/xaml/hh465373.aspx).
APPHOST9603: „Can't load the ActiveX plug-in that has the class ID *classID*.  Apps can't load ActiveX controls.“ (Das ActiveX-Plug-In mit der Klassen-ID „KlassenID“ konnte nicht geladen werden. Apps können keine ActiveX-Steuerelemente laden.) | Windows-Runtime-Apps mit JavaScript unterstützen keine benutzerdefinierten ActiveX-Steuerelemente von Microsoft. Wenn Sie ein UI-Steuerelement benötigen, können Sie ein standardmäßiges Websteuerelement oder eine Bibliothek für Steuerelemente verwenden oder Ihr eigenes benutzerdefiniertes Steuerelement erstellen. Wenn Sie benutzerdefinierte Logik ausführen müssen, können Sie stattdessen ein benutzerdefiniertes Windows-Runtime-Objekt erstellen. Informationen zu weiteren Unterschieden zwischen HTML, CSS und JavaScript finden Sie unter [HTML, CSS und JavaScript – Features und Unterschiede](https://msdn.microsoft.com/en-us/library/windows/apps/xaml/hh465380.aspx).
APPHOST9604: „Can't navigate to *uri* because it uses an invalid character encoding.  An app can navigate only to UTF8-encoded files.“ (Keine Navigation zu „uri“ möglich, da eine ungültige Zeichencodierung verwendet wird. Eine App kann nur zu UTF8-codierten Dateien navigieren.) | Wenn Windows-Runtime auf HTML, JavaScript und CSS zugreifen soll, müssen diese im UTF-8-Format (8-Bit-Unicode Transformation Format) codiert sein. Informationen zu weiteren Unterschieden zwischen HTML, CSS und JavaScript finden Sie unter [HTML, CSS und JavaScript – Features und Unterschiede](https://msdn.microsoft.com/en-us/library/windows/apps/xaml/hh465380.aspx).
APPHOST9605: „Can't navigate to *targetURI* from *sourceURI* because the destination URI is in a higher security zone. You can't navigate from a zone with lower security to a zone with higher security unless you're navigating to a local context URI from a web context URI and you've registered the local context URI with the MSApp.addPublicLocalApplicationUri method.“ (Keine Navigation von „QuellURI“ zu „ZielURI“ möglich, da sich der Ziel-URI in einem Bereich mit höherer Sicherheit befindet. Sie können nur von einem Bereich mit niedrigerer Sicherheit zu einem Bereich mit höherer Sicherheit navigieren, wenn Sie von einem Webkontext-URI zu einem URI im lokalen Kontext navigieren und den URI im lokalen Kontext mit der MSApp.addPublicLocalApplicationUri-Methode registriert haben.) | Weitere Informationen finden Sie unter [addPublicLocalApplicationUri method (addPublicLocalApplicationUri-Methode)](https://msdn.microsoft.com/en-us/library/windows/apps/xaml/hh465759.aspx).
APPHOST9606: „Can't load *uri* because it uses an HTTP connection and the ms-https-connections-only meta element is present. Only HTTPS connections are allowed when you use the ms-https-connections-only meta element. Use an HTTPS connection or, if you don't need a secure connection, remove the meta element.“ („uri“ konnte nicht geladen werden, da eine HTTP-Verbindung verwendet wird und das Metaelement „ms-https-connections-only“ vorhanden ist. Bei Verwendung des Metaelements „ms-https-connections-only“ sind nur HTTPS-Verbindungen zulässig. Verwenden Sie eine HTTPS-Verbindung, oder entfernen Sie das Metaelement, falls keine sichere Verbindung benötigt wird.) | Weitere Informationen finden Sie unter [Anfordern einer HTTPS-Verbindung](https://msdn.microsoft.com/en-us/library/windows/apps/xaml/hh452771.aspx).
APPHOST9607: „The app can't launch the URI at *uri* because of this error: *failureCode*.“ (Die App kann den URI bei „uri“ wegen folgendem Fehler nicht starten: „FehlerCode“.) | Eine fehlende Ressource oder eine ungültige Datei sind häufige Ursachen dieses Fehlers.
APPHOST9608: „The app couldn't navigate to the about:blank page because of this error: *errorCode*.“ (Die App konnte wegen folgendem Fehler nicht zur about:blank-Seite navigieren: „FehlerCode“.) | 
APPHOST9610: „The app found an error while preparing to navigate to a custom error page: *errorCode*.“ (Die App hat bei der Vorbereitung der Navigation zu einer benutzerdefinierten Fehlerseite einen Fehler gefunden: „FehlerCode“.) |
APPHOST9611: „The app couldn't navigate to a custom error page because of this error: *errorCode*.“ (Die App konnte wegen folgendem Fehler nicht zu einer benutzerdefinierten Fehlerseite navigieren: „FehlerCode“.) |
APPHOST9613: „The app couldn't navigate to *uri* because of this error: *errorCode*.“ (Die App konnte wegen folgendem Fehler nicht zu *uri* navigieren: „FehlerCode“.) | 
APPHOST9614: „A document within an iframe requested the *requestedDocMode* doc mode, but the system enforces the *currentDocMode* doc mode. The iframe will use the *currentDocMode* doc mode.“ (Ein Dokument in einem IFrame hat den Dokumentmodus „angeforderterDokumentmodus“ angefordert, vom System wird jedoch der Dokumentmodus „aktuellerDokumentmodus“ erzwungen. Der IFrame verwendet den Dokumentmodus „aktuellerDokumentmodus“.) | Weitere Informationen zum Anzeigen von Remotewebinhalten finden Sie unter [Verknüpfen mit externen Webseiten](https://msdn.microsoft.com/en-us/library/windows/apps/xaml/hh780594.aspx).
APPHOST9615: „The app can't download the file at *uri* because it was invoked programmatically outside of the local context.“ (Die App konnte die Datei bei „uri“ nicht herunterladen, da sie programmgesteuert außerhalb des lokalen Kontexts aufgerufen wurde.) | Tritt auf, wenn Inhalt im Webkontext versucht, eine Datei programmgesteuert herunterzuladen.
APPHOST9616: „This URI can't use geolocation APIs.  Geolocation APIs can be invoked only from a URI that is part of the package or is included in the ApplicationContentUris element of the manifest.“ (Dieser URI kann keine Geolocation-APIs verwenden. Geolocation-APIs können nur von einem URI aufgerufen werden, der Teil des Paktes ist oder im ApplicationContentUris-Element des Manifests enthalten ist.) | Weitere Informationen darüber, was im Webkontext zulässig ist, finden Sie unter [Features und Einschränkungen nach Kontext](https://msdn.microsoft.com/en-us/library/windows/apps/xaml/hh465373.aspx).
APPHOST9617: „This URI can't use clipboard APIs.  The clipboard APIs can be invoked only from a URI that is part of the package or is included in the ApplicationContentUris element of the manifest.“ (Dieser URI kann keine Clipboard-APIs verwenden. Clipboard-APIs können nur von einem URI aufgerufen werden, der Teil des Paktes ist oder im ApplicationContentUris-Element des Manifests enthalten ist.) | Weitere Informationen darüber, was im Webkontext zulässig ist, finden Sie unter [Features und Einschränkungen nach Kontext](https://msdn.microsoft.com/en-us/library/windows/apps/xaml/hh465373.aspx).
APPHOST9618: „This URI can't use window.close.  The window.close method can be invoked only from packaged content that was loaded with an ms-appx URI scheme.“ (Dieser URI kann „window.close“ nicht verwenden. Die „window.close“-Methode kann nur von Paketinhalten aufgerufen werden, die mit dem URI-Schema „ms-appx“ geladen wurden.) | Weitere Informationen darüber, was im Webkontext zulässig ist, finden Sie unter [Features und Einschränkungen nach Kontext](https://msdn.microsoft.com/en-us/library/windows/apps/xaml/hh465373.aspx).
APPHOST9619: „The app can't navigate to *uri* because a page in the web context can't be the app's top level document. Load the page in an iframe instead.“ (Die App konnte nicht zu „uri“ navigieren, da eine Seite im Webkontext nicht das Dokument auf oberster Ebene der App sein kann. Laden Sie die Seite stattdessen in einem IFrame.) | Sie können Ihre Seite auf oberster Ebene nicht zu einer Remotewebseite navigieren, aber Ihre App kann eine Webseite in einem [IFrame](https://msdn.microsoft.com/en-us/library/ms535258(v=vs.85).aspx) anzeigen. Weitere Informationen zum Anzeigen von Remotewebinhalten finden Sie unter [Verknüpfen mit externen Webseiten](https://msdn.microsoft.com/en-us/library/windows/apps/xaml/hh780594.aspx).
APPHOST9620: „This app was closed because it used an HTTP connection and the ms-https-connections-only meta element is present. Only HTTPS connections are allowed when you use the ms-https-connections-only meta element. Use an HTTPS connection or, if you don't require a secure connection, remove the meta element.“ (Diese App wurde beendet, da eine HTTP-Verbindung verwendet wurde und das Metaelement „ms-https-connections-only“ vorhanden ist. Bei Verwendung des Metaelements „ms-https-connections-only“ sind nur HTTPS-Verbindungen zulässig. Verwenden Sie eine HTTPS-Verbindung, oder entfernen Sie das Metaelement, falls keine sichere Verbindung benötigt wird.) | Weitere Informationen finden Sie unter [Anfordern einer HTTPS-Verbindung](https://msdn.microsoft.com/en-us/library/windows/apps/xaml/hh452771.aspx).
APPHOST9623: „The app couldn't resolve *url* because of this error: *errorCode*.“ (Die App konnte „URL“ wegen folgendem Fehler nicht auflösen: „FehlerCode“.) | Eine häufige Ursache dieses Fehlers ist eine fehlende Datei.  
APPHOST9624: „The app can't use script to load the *url* url because the url launches another app. Only direct user interaction can launch another app.“ (Die App konnte das Skript nicht zum Laden der URL „URL“ verwenden, da die URL eine andere App startet. Eine andere App kann nur durch direkte Benutzerinteraktion gestartet werden.) | Apps können andere Apps nicht direkt starten. Andere Apps können vom Benutzer gestartet werden, wenn die Apps bestimmte Verträge implementieren. Weitere Informationen finden Sie unter [App-Verträge und -Erweiterungen](https://msdn.microsoft.com/en-us/library/windows/apps/xaml/hh464906.aspx).
APPHOST9626: „A direct reference to resource file `ms-appx://1d33240b-0b00-40e4-a416-a4750c48787f/ja-jp\images\logo.scale-140.png` was detected. This reference causes failures when used outside of the debugging environment.“ (Ein direkter Verweis auf die Ressourcendatei „ms-appx://1d33240b-0b00-40e4-a416-a4750c48787f/ja-jp\images\logo.scale-140.png“ wurde erkannt. Dieser Verweis führt außerhalb der Debugumgebung zu Fehlern.) | Aufgrund des Dateipfads von `logo.scale-140.png` wird diese PNG-Datei als lokalisierte Ressource behandelt, was einen Fehler verursacht, da auf lokalisierte Ressourcen nicht direkt verwiesen werden kann. Wenn Sie diese Datei als Sprachressource verwenden möchten, finden Sie dazu Informationen unter [Globalisieren Ihrer App (HTML)](https://msdn.microsoft.com/en-us/library/windows/apps/xaml/hh465006.aspx). Versuchen Sie andernfalls, das problematische Verzeichnis umzubenennen.
  
## <a name="see-also"></a>Siehe auch  
 [Verwenden von Windows-Runtime in JavaScript](../jswinrt/using-the-windows-runtime-in-javascript.md)
