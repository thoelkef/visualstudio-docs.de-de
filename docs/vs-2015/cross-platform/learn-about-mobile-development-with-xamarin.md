---
title: Erfahren Sie mehr über die Entwicklung für mobile Plattformen mit Xamarin | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.topic: conceptual
ms.assetid: e970d936-1df4-4c0c-96e3-ef6191295882
caps.latest.revision: 14
ms.author: crdun
manager: crdun
ms.openlocfilehash: a362bd4eef2a48667c67c03e940e213fc960418b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "75919004"
---
# <a name="learn-about-mobile-development-with-xamarin"></a>Erfahren Sie mehr über die Entwicklung für mobile Plattformen mit Xamarin
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Dieses Thema führt Sie zu Unterrichtsmaterial, das Ihnen die Grundlagen des Entwickelns von plattformübergreifenden mobilen Apps mit Xamarin vermittelt. Wenn Sie Visual Studio und Xamarin noch nicht installiert haben, starten Sie zuerst den [Setup und Installation](../cross-platform/setup-and-install.md) -Prozess, und kehren Sie dann hierher zurück, um sich durch diese Ressourcen zu arbeiten, während die Installationsprogramme ausgeführt werden.  
  
> [!NOTE]
> Falls nicht anders beschrieben, empfehlen wir Ihnen, sich anfangs auf die hier direkt verlinkten Seiten zu beschränken und Unterseiten zunächst zu ignorieren. Wenn der Installationsvorgang nach dem Durcharbeiten dieser Liste immer noch ausgeführt wird, können Sie hierher zurückkehren und weitere Themen erforschen.  
>   
> Außerdem kann es sinnvoll sein, die mit „Grundlagen“ überschriebenen Themen zu lesen und später zu den „Vertiefung“-Themen zurückzukehren.  
  
## <a name="essentials-introduction-to-xamarin"></a>Grundlagen: Einführung in Xamarin  
 *10–20 Minuten*  
  
1. [Mobile Apps in Visual Studio mit Xamarin](https://www.visualstudio.com/explore/xamarin-vs) (visualstudio.com) bietet eine sehr kurze Zusammenfassung der Hauptmerkmale von Xamarin.  
  
2. [Erstellen von plattformübergreifenden mobilen Apps mithilfe von C# und Visual Studio](https://channel9.msdn.com/Events/Visual-Studio/Visual-Studio-2015-Final-Release-Event/Building-cross-platform-mobile-apps-using-C-and-Visual-Studio-2015) (Channel9, 15 m 16 s) mit Xamarin-Evangelist James Montemagno. Die ersten drei Minuten geben einen Überblick zu Xamarin, gefolgt von Codedemonstrationen.  
  
## <a name="essentials-overview-of-the-visual-studio-and-xamarin-environment"></a>Grundlagen: Übersicht der Visual Studio- und Xamarin-Umgebung  
 *5–15 Minuten*  
  
- Den größten Teil Ihrer Arbeit verrichten Sie am Windows-Computer mit Visual Studio und Xamarin. Auf diesem Computer erstellen Sie Windows- und Android-Apps direkt und führen sie auf einem Gerät oder einem Emulator aus, auf denen auch das Debuggen erfolgt. Ferner können Sie auf einem Mac iOS-Apps remote erstellen, ausführen und debuggen. Visual Studio auf einem Windows-Computer kann darüber hinaus eine Verbindung mit dem iOS Storyboard-Designer und dem iOS-Simulator herstellen.  
  
- Der Mac mit Xcode und Xamarin dient als Build- und Signaturhost sowie als Laufzeitumgebung für iOS-Apps. Builds für iOS von Visual Studio auf dem Windows-Computer werden an diesen Mac delegiert. Beim Debuggen einer iOS-App in Visual Studio erfolgt die Ausführung im iOS-Simulator auf dem Mac oder direkt auf einem mit dem Mac verbundenen Gerät. In diesem Fall interagieren Sie mit der App auf dem Mac oder in dessen Nähe, während die Debugoberfläche in Visual Studio ist.  
  
  Diese Beziehungen sind unten dargestellt, und Sie finden weitere Informationen über das Arbeiten mit iOS-Apps unter [Introduction to Xamarin.iOS for Visual Studio](/xamarin/ios/get-started/installation/windows/introduction-to-xamarin-ios-for-visual-studio) (xamarin.com).  
  
  ![Die Beziehung zwischen Windows-und Mac-Entwicklungs Computern in einer xamarin-Umgebung](../cross-platform/media/crossplat-xamarin-learn-1.png "Crossplat xamarin Learn 1")  
  
## <a name="essentials-how-projects-are-structured"></a>Grundlagen: Strukturieren von Projekten  
 *10–30 Minuten*  
  
1. [Sharing Code Options](/xamarin/cross-platform/app-fundamentals/code-sharing) (xamarin.com). Wir empfehlen, die Option mit portablen Klassenbibliotheken zu wählen, da sie am besten die Verwendung genau nur der .NET-APIs unterstützt, die auf allen Zielplattformen unterstützt werden. Der größte Teil des Code für Geschäftslogik befindet sich in der PCL, einschließlich des Zugriffs auf Datenbanken, in Aufrufen von REST-APIs und in Aufrufen von portablen Xamarin-Komponenten (siehe [Deeper Dive: Xamarin Components](#components) am Ende dieses Themas). Gemeinsamer Code der Benutzeroberfläche, der mit Xamarin.Forms erstellt wurde, kann sich ebenfalls in einer PCL befinden.  
  
2. (Optional) In [Case Study: Tasky](/xamarin/cross-platform/app-fundamentals/building-cross-platform-applications/case-study-tasky) (xamarin.com) sind einige bewährte Methoden zum Entwerfen und Strukturieren einer vollständigen App beschrieben, etwa das Strukturieren des Projekts mit einer PCL für freigegebenen Code, in dem Daten, Datenzugriff und Geschäftsschichten voneinander getrennt sind.  
  
## <a name="essentials-native-and-xamarinforms-ui-layers"></a>Grundlagen: Xamarin Native- und Xamarin.Forms-Benutzeroberflächenebenen  
 *10-40 Minuten*  
  
 Xamarin bietet zwei Möglichkeiten, großartige systemeigene Apps zu erstellen: Xamarin Native und Xamarin.Forms.  
  
 Mit Xamarin Native schreiben Sie getrennten Benutzeroberflächencode für jede Zielplattform: iOS, Android und Windows.  Mit diesem Ansatz haben Sie direkten Zugriff auf plattformspezifische APIs, wodurch eine angepasste Benutzeroberfläche pro Plattform ermöglicht wird.  Außerdem haben Sie vollständigen Zugriff auf den systemeigenen Designer und die systemeigenen Steuerelemente für jede Plattform als Unterstützung beim Erstellen der entsprechenden Benutzeroberfläche.  
  
 Xamarin.Forms stellt einen allgemeinen Satz von APIs bereit, mit denen Sie eine gemeinsam genutzte Benutzeroberflächenebene für alle Plattformen in einer portablen Klassenbibliothek schreiben können.  Xamarin.Forms rendert in systemeigene Steuerelemente für jede Zielplattform, um ein systemeigenes Aussehen und Verhalten zu erzielen.  Wenn Sie Xamarin.Forms verwenden, arbeiten Sie nicht mit einem Designer, sondern Sie erstellen Ihre Benutzeroberfläche mit C# und XAML.  
  
 Sie müssen nicht im Voraus entscheiden, welchen Ansatz Sie wählen. Apps können mit einer Kombination aus Xamarin Native und Xamarin.Forms implementiert werden:  
  
- Verwenden Sie Xamarin.Forms, um für allgemeine Zwecke vorgesehene Bildschirme zu erstellen, die eine ähnliche Benutzeroberfläche und Funktionalität über Plattformen hinweg bereitstellen, etwa Anmeldungen, Kontaktformulare und Suchergebnisse.  
  
- Verwenden Sie eine Vielzahl von Anpassungsfunktionen in Xamarin.Forms, um die Benutzeroberfläche plattformspezifisch anzupassen. Hierzu gehören die OnPlatform-API, die sowohl in Code als auch in XAML verwendet werden kann, und mit der eine benutzerdefinierte Ansicht erstellt, ein vorhandener Renderer erweitert und ein benutzerdefinierter Renderer erstellt werden kann.  
  
- Verwenden Sie bei Bedarf Xamarin Native, um Bildschirme zu erstellen, die spezielle Benutzeroberflächenfunktionen jeder Plattform verwenden, beispielsweise ein Bildschirm, für den native Kameraaufnahme oder Bildbearbeitung verwendet wird.  
  
  Es empfiehlt sich, mit einer Xamarin.Forms-Projektmappe zu beginnen, um Benutzeroberflächencode zu schreiben, der für alle Plattformen gemeinsam verwendet werden kann, und dann die Anpassungsmöglichkeiten zu verwenden, um plattformspezifische Anpassungen vorzunehmen. Sofern Sie vollständig plattformspezifische Bildschirme benötigen, können Sie diese einzeln mit Xamarin Native hinzufügen.  
  
  Weitere Informationen:  
  
1. [Xamarin.Forms](/xamarin/xamarin-forms/) (xamarin.com) stellt die Vor- und Nachteile von Xamarin.Forms im Vergleich zu systemeigenen Benutzeroberflächenschichten (d. h., Xamarin.iOS und Xamarin.Android) in einer kurzen Übersicht vor.  
  
2. Die ersten drei Minuten von James Montemagno Video [xamarin. Forms: Native IOS, Android & Windows-apps mit c# & XAML](https://channel9.msdn.com/events/Visual-Studio/Connect-event-2015/704) (Channel9, 13m3s) bieten eine weitere Übersicht, und Sie können weiterhin Demos ansehen.  
  
3. (Optional) [An Introduction to Xamarin.Forms](/xamarin/get-started/quickstarts/deepdive?pivots=windows) (xamarin.com).  
  
4. (Optional) Beispiele, wie Sie mit OnPlatform Anpassungen vornehmen können, finden Sie in der Dokumentation von [Device Class](/xamarin/xamarin-forms/platform/device) (xamarin.com).  
  
5. (Optional) In [Gemeinsames Verwenden von Benutzeroberflächencode auf mobilen Plattformen mit Xamarin.Forms](https://msdn.microsoft.com/magazine/dn904669.aspx) von Jason Smith (MSDN Magazin) sind die verschiedenen Anpassungsoptionen skizziert, die es in Xamarin.Forms gibt. Ausführlichere Informationen zu diesen Optionen finden Sie unter [Customizing Controls on Each Platform](/xamarin/xamarin-forms/app-fundamentals/custom-renderer/) (xamarin.com).  
  
## <a name="deeper-dive-debugging-with-emulators"></a>Vertiefung: Debuggen mit Emulatoren  
 *10–15 Minuten*  
  
 Wenn Sie plattformübergreifende Apps debuggen möchten, ohne ein physisches Gerät zu verwenden, müssen Sie folgendes Tool verwenden:  
  
1. **Ein Android-Emulator.** Je nachdem, mit welcher Version von Windows Sie arbeiten, sollten Sie entweder Microsofts Visual Studio Emulator für Android oder den Xamarin Player verwenden, die beide hohe Leistung bieten und eine Vielzahl von Gerätefunktionen unterstützen:  
  
    - **Computer mit Windows 8+:** Es wird dringend empfohlen, Microsofts [Visual Studio Emulator für Android](https://www.visualstudio.com/features/msft-android-emulator-vs.aspx)zu verwenden, der mit Visual Studio installiert wurde.  Das Video zum [Visual Studio-Emulator für Android](https://channel9.msdn.com/events/Visual-Studio/Connect-event-2015/711) (Channel9, 5m55s) bietet eine Übersicht und eine Demonstration.  
  
    - **Windows 7 oder früher/Windows unter Mac OS X**: Verwenden Sie den [Xamarin Android Player](/xamarin/android/deploy-test/debugging/debug-on-emulator?tabs=windows) (xamarin.com).  
  
2. **IOS-Simulator von Apple.** Weitere Informationen hierzu finden Sie unter [Getting Started in Simulator (Erste Schritte im Simulator)](https://developer.apple.com/library/prerelease/content/documentation/IDEs/Conceptual/iOS_Simulator_Guide/GettingStartedwithiOSSimulator/GettingStartedwithiOSSimulator.html#//apple_ref/doc/uid/TP40012848-CH5-SW1) (apple.com).  
  
3. **Microsoft Windows Phone Emulator.** Weitere Informationen hierzu finden Sie unter [Ausführen von Windows Phone-Apps im Emulator](https://msdn.microsoft.com/library/dn632391.aspx).  
  
## <a name="deeper-dive-xamarin-components"></a><a name="components"></a> Tieferer Einblick: xamarin-Komponenten  
 *10 Minuten*  
  
 Viele erweiterte Leistungsmerkmale stehen Xamarin-Apps über Xamarin-Komponenten zur Verfügung. Den vollständigen Katalog, der für den Download verfügbar [http://components.xamarin.com/](/xamarin/cross-platform/troubleshooting/component-nuget?tabs=windows) ist, finden Sie unter. Dies umfasst Komponenten für zusätzliche Steuerelemente der Benutzeroberfläche, Authentifizierung, eine Vielzahl von Clouddiensten wie Microsoft Azure und vieles mehr.
