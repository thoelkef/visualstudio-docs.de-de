---
title: "Vorteile von Visual Studio für Mac gegenüber Xamarin Studio"
author: asb3993
ms.author: amburns
ms.date: 04/14/2017
ms.topic: article
ms.assetid: 6ACF5FD4-D5C1-4050-95E3-467C753F25F1
ms.translationtype: HT
ms.sourcegitcommit: f6c7e290f0abc2c32456e076420a7695ae868ba6
ms.openlocfilehash: 655795fd64958805e0137d7e231391c59f676776
ms.contentlocale: de-de
ms.lasthandoff: 09/26/2017

---

# <a name="benefits-of-visual-studio-for-mac-over-xamarin-studio"></a>Vorteile von Visual Studio für Mac gegenüber Xamarin Studio 
 
Visual Studio für Mac ersetzt Xamarin Studio als vollständige IDE unter Mac. Es bietet Features, mit denen Sie Webanwendungen und -dienste, plattformübergreifende mobile und Desktop-Apps sowie Spiele entwickeln können. Darüber hinaus ist die Integration in Azure eine Leichtigkeit – sei es das Veröffentlichen in Azure oder das Erstellen von Azure Functions. Es kommt mit allem, was Sie sich von einer modernen IDE erhoffen können – einem vollständigen Quellcode-Editor, Codesuche und -navigation, einem leistungsstarken Debugger, einem anpassbaren Arbeitsbereich, Git-Integration und einem umfangreichen Angebot an Erweiterungen, die alle nativ für Mac entwickelt wurden. 

Einige weitere Funktionen: 

* Roslyn-basiertes C#-IntelliSense, Refactoring, Analyzer und Codekorrekturen 
* NuGet-basierte Paketverwaltung 
* Mit Visual Studio kompatibles Projektformat 
* MSBuild-Modul 
* Integrierte Unittests 
* Unterstützung für gebrauchsfertiges F# 

Vorteile, die in diesem Handbuch als **Vorschauversionen** gekennzeichnet sind, sind nur im [Alphakanal](https://docs.microsoft.com/en-us/visualstudio/mac/update#Changing_the_Updater_channel) verfügbar. 

## <a name="language-support"></a>Sprachenunterstützung 

Das Schreiben von C# 7-Code auf Ihrem Mac wird nur für Visual Studio für Mac angeboten.

## <a name="net-core"></a>.NET Core  

[.NET Core](https://www.microsoft.com/net/core#macos) ist eine Plattform zum Erstellen von Anwendungen, die sowohl unter Windows und Linux als auch unter Mac ausgeführt werden können. Visual Studio für Mac verfügt über Unterstützung für das Laden, Erstellen, Ausführen und Debuggen von .NET Core-Projekten. 

.NET Core wird mit Visual Studio für Mac installiert und ist sofort einsatzbereit.

Die .NET Core-Unterstützung enthält: 

* C# und F#-IntelliSense 
* .NET Core-Projektvorlagen für Konsolen, Bibliotheken und Webanwendungen 
* Vollständige Unterstützung beim Debuggen, u.a. Haltepunkte, Aufruflisten, Überwachungsfenster, usw. 
* NuGet-Paketverweise und MSBuild-basiertes Wiederherstellen 
* Integrierte Unterstützung von Unittests für das Ausführen und Debuggen von Tests mit der Visual Studio-Testplattform, die im .NET Core SDK enthalten ist. 
* Migration vom alten project.json-Format 
* .NET Standard-Projektunterstützung

## <a name="web-development"></a>Webentwicklung  

### <a name="aspnet-core"></a>ASP.NET Core 

Visual Studio für Mac enthält ASP.NET Core-Vorlagen für gebrauchsfertige MVC und Web-API-Projekte.
 
![HTML-IntelliSense](media/benefits-vsmac-over-xs-image3.png)

Mit Visual Studio für Mac wird zudem eine neue Unterstützung von Tools für die Entwicklung von Webanwendungen für HTML-, CSS- und JSON-Dateien eingeführt. 

### <a name="html"></a>HTML 

* Neue HTML-Vorlag 
* Verbesserung des intelligenten Einzugs und der intelligenten Formatierung 
* Verbesserung der Farbgebung 
* Verbesserung von IntelliSense 
* Codefaltung (muss aktiviert sein) 
* Befehl „Unminify“ (Aufheben der Minimierung) 
* Verbesserung der Codevorlagen (Ausschnitte) 
* Auswahl mit `<div>` umschließen. 
* Mit der Option „Up/Down“ (Oben/Unten) kann Text nach oben/unten verschoben werden. 

### <a name="css"></a>CSS 

* Verbesserung des intelligenten Einzugs und der intelligenten Formatierung 
* Verbesserung der Farbgebung 
* Verbesserung von IntelliSense 
* Codefaltung 
* Viele Codevorlagen (Ausschnitte) 
* Mit der Option „Up/Down“ (Oben/Unten) kann Text nach oben/unten verschoben werden. 

### <a name="json"></a>JSON 
* Schemaauswahl mit Zugriff auf „schemastore.org“ 
* Validierung aus einem Schema 
* IntelliSense aus einem Schema 
* Verbesserung des intelligenten Einzugs und der intelligenten Formatierung 
* Verbesserung der Farbgebung 
* Auskommentierung/Auskommentierung aufheben 
* Einfügung von Anführungszeichen und zugehörigen Klammern 
* Mit der Option „Up/Down“ (Oben/Unten) kann Text nach oben/unten verschoben werden. 

## <a name="publishing-to-azure"></a>Veröffentlichen in Azure

Mit Visual Studio für Mac ist die Veröffentlichung Ihrer ASP.NET Core-Webanwendungen und -dienste in Azure App Service. 

![Veröffentlichen in Azure](media/benefits-vsmac-over-xs-image1.png)

### <a name="azure-functions-preview"></a>Azure Functions (**Vorschauversion**)

Azure Functions ist eine Lösung zum einfachen Ausführen kleiner Codestücke oder „Funktionen“ in der Cloud. Mit Visual Studio für Mac können Sie Ihre Azure Functions codieren und lokal debuggen. Beginnen Sie, indem Sie im unter „Cloud“ im Dialogfeld „Neues Projekt“ nach Azure Functions suchen. 

### <a name="docker-support-preview"></a>Docker-Unterstützung (**Vorschauversion**)

Sie können jetzt ASP.NET Core-Apps in Docker-Containern veröffentlichen und sie in einem Azure App Service ausführen. 

Um die Docker-Unterstützung in Ihrem Projekt zu aktivieren, klicken Sie mit der rechten Maustaste auf Ihre ASP.NET Core-Webanwendung und dann auf **Hinzufügen > Docker-Unterstützung hinzufügen**. 

Um Ihre Webanwendung in einem Docker-Container zu veröffentlichen, verwenden sie den Arbeitsfluss **Veröffentlichen > In Azure veröffentlichen**, der in Visual Studio für Mac eingeführt wurde.

## <a name="source-editor-improvements"></a>Optimierungen des Quell-Editors 

Zusätzlich zu Roslyn-basiertem C#-IntelliSense, Refactoring, Analyzern und Codekorrekturen wurde der Quell-Editor von Visual Studio für Mac im Vergleich zu Xamarin Studio folgendermaßen verbessert: 

### <a name="language-bundles"></a>Sprachbündel 

Visual Studio für Mac verfügt über Unterstützung für TextMate-Sprachbündel (`.tmBundle`) und Sprachbündel von Sublime 3 (`.sublime`), die Sie zum Hinzufügen von Folgendem verwenden können: 

* Farbdesigns im Editor 
* Codeausschnitte 
* Grammatik für neue Sprachen, wodurch das Markieren und grundlegendes IntelliSense aktiviert werden 

Sie können diese Bündel unter **Einstellungen > Text-Editor > Sprachbündel** hinzufügen. 

### <a name="color-theme-support"></a>Farbdesignunterstützung 

Folgende Farbdesignformate werden in Visual Studio für Mac unterstützt: 

* Visual Studio (`.vssettings`) 
* Xamarin Studio (`.json`) 
* TextMate (`tmTheme`) 

## <a name="unity"></a>Unity 

[Unity](https://unity3d.com/) ist ein Tool zum Erstellen von Spielen, mit dem Sie qualitativ hochwertige, plattformübergreifende 2D- und 3D- Spiele für alle gängigen Plattformen erstellen können: für mobile, Desktop-, Konsolen-, AR- und VR-Geräte und sogar fürs Web. 

Ab Unity 5.6.1 können Sie Visual Studio für Mac verwenden, um Unity-Spiele zu schreiben und zu debuggen. Beginnen Sie, indem Sie Visual Studio als Skript-Editor von Unity 5.6.1 festlegen. 

Tools von Unity sind unter anderem: 

* die Unterstützung für in C# geschriebenes Skript 
* das Projektmappenpad von Unity 
* das Debuggen mit einem Klick vom Unity-Editor 
* Nachrichten von IntelliSense für Unity 
* Codeeinfärbung für Shader von Unity 
* Zugriff auf die Dokumentation zu Unity 

## <a name="xamarin"></a>Xamarin 

Während die plattformübergreifenden Features von Xamarin schon immer ein erstklassiges Feature von Xamarin Studio waren, gibt es nun auch Xamarin-Features, die nur in Visual Studio für Mac zur Verfügung stehen. 

### <a name="android"></a>Android 

* [Android-SDK-manager](https://developer.xamarin.com/guides/android/application_fundamentals/using-the-sdk-manager/)  
* Android O wird nur in Visual Studio für Mac und nicht in Xamarin Studio unterstützt. 

### <a name="ios-and-mac"></a>iOS und Mac 

* [Aktualisierungen des Signierungsworkflows unter iOS](https://developer.xamarin.com/guides/cross-platform/macios/apple-account-management/) 
    * Erstellen Sie neue Signierungsidentitäten und installieren Sie diese im lokalen Schlüsselbund. 
    * Erstellen Sie Bereitstellungsprofile. 
    * Fügen Sie eine neue Signierungsidentitäten zu einem vorhandenen Profil hinzu.
    *  Stellen Sie Geräte bereit: Registrieren Sie ein Gerät im Apple-Entwicklerportal, und fügen Sie diese einem Bereitstellungsprofil hinzu.
* iOS 11, watchOS 4 und tvOS 2 werden nur in Visual Studio für Mac und nicht in Xamarin Studio unterstützt. 
* MacOS High Sierra wird nur in Visual Studio für Mac und nicht in Xamarin Studio unterstützt. 

### <a name="cross-platform"></a>Plattformübergreifend 

* [Xamarin Live Player](https://developer.xamarin.com/guides/cross-platform/live/) (**Vorschauversion**) 
* [Xamarin IoT](https://developer.xamarin.com/guides/cross-platform/iot/) (**Vorschauversion**) 
 
