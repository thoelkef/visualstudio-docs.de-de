---
title: Setup, Installation und Überprüfungen für Mac-Benutzer | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.topic: conceptual
ms.assetid: 22725520-59ba-4f6f-80e4-097b1287a34b
caps.latest.revision: 14
ms.author: crdun
manager: crdun
ms.openlocfilehash: 52310ffb0a3c08f652f4d628db1c047a5d0417d6
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2019
ms.locfileid: "54772034"
---
# <a name="setup-install-and-verifications-for-mac-users"></a>Setup, Installation und Überprüfungen für Mac-Benutzer
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Dieses Thema ist für Entwickler bestimmt, die hauptsächlich auf einem Mac arbeiten und Visual Studio optional innerhalb eines virtuellen Windows-Computers auf dem Mac verwenden. Wenn Sie ein Entwickler sind, der hauptsächlich auf einem Windows-Computer arbeitet, und einen sekundären Mac für die Zielplattform iOS einrichten müssen, lesen Sie das Hauptthema [Setup und Installation](../cross-platform/setup-and-install.md).  
  
 Um mit Xamarin auf einem Mac zu arbeiten, benötigen Sie Folgendes:  
  
- Ein Xamarin-Konto. Wechseln Sie zu [ https://www.xamarin.com/ ](https://www.xamarin.com/) , und klicken Sie auf **Anmeldung** oben rechts auf der Seite, klicken Sie dann auf **Erstellen eines neuen Kontos** auf der Seite, die angezeigt wird. Wählen Sie eine E-Mail-Adresse und das Kennwort für Ihr Xamarin-Konto aus.  
  
- Einen Mac mit OSX Yosemite (10.10) oder höher mit installiertem Xcode 7 und Xamarin 4.  
  
- Eine der folgenden Konfigurationen:  
  
  -   **Für ausgeführte Xamarin.Studio direkt auf dem Mac:** Xamarin Studio ist Xamarins-Entwicklungsumgebung, die die Erstellung unterstützt Android, iOS und Windows-apps mithilfe von C#.  Einen schnellen Überblick zu Xamarin Studio finden Sie unter [Xamarin Studio Overview](https://xamarin.com/studio) (xamarin.com).  
  
  -   **Wenn auf Ihrem Mac bereits Parallels oder VMWare installiert ist:** Führen Sie Windows mit Visual Studio 2015 und Xamarin 4 innerhalb von Parallels oder VMWare aus.  Bei dieser Konfiguration stellt Xamarin eine Erweiterung dar, die zusammen mit Visual Studio installiert wird und die Möglichkeit bereitstellt, Visual Studio als Ihre Entwicklungsumgebung für das Erstellen von Android-, iOS- und WinPhone-Apps mithilfe von C# zu verwenden.  Beachten Sie, dass Sie im Rahmen des Visual Studio Developer Essentials-Programms ein kostenloses Parallels-Abonnement für drei Monate erhalten können. Mehr dazu können Sie unter [Microsoft Visual Studio Dev Essentials Will Include Parallels Desktop Pro and Parallels Access](http://blog.parallels.com/blog/2015/11/18/visual-studio-dev-essentials/) [Microsoft Visual Studio Dev Essentials beinhaltet zukünftig auch Parallels Desktop Pro und Parallels Access] (Parallels-Blog) erfahren.  
  
  Dieses Thema enthält die Anweisungen zu diesen Anforderungen.  Während der Installationsvorgang ausgeführt wird, können Sie das Thema [Erfahren Sie mehr über die Entwicklung für mobile Plattformen mit Xamarin](../cross-platform/learn-about-mobile-development-with-xamarin.md) durcharbeiten, um das erforderliche Hintergrundmaterial zu lesen und anzusehen.  
  
  **In diesem Thema:**  
  
- [Mac-Setup (Apple ID, Xcode und Xamarin)](#mac)  
  
- [Windows-Setup innerhalb von Parallels (Visual Studio und Xamarin)](#windows)  
  
- [Überprüfen der Umgebung](#verify)  
  
##  <a name="mac"></a> Mac-Setup (Apple ID, Xcode und Xamarin)  
  
1.  Erstellen Sie eine kostenlose Apple ID unter [My Apple ID](https://appleid.apple.com/) , wenn Sie noch keine besitzen. Dies ist für die Installation von und die Anmeldung bei Xcode erforderlich.  
  
2.  Laden Sie Xcode von [https://developer.apple.com/xcode/](https://developer.apple.com/xcode/) herunter, und führen Sie die Installation durch.  
  
3.  Laden Sie Xamarin herunter, und installieren Sie es, indem Sie die Anweisungen unter [Installing and Configuring Xamarin.iOS](http://developer.xamarin.com/guides/ios/getting_started/installation/mac/) (xamarin.com) befolgen.  
  
4.  Sobald Sie die Installation von Xamarin auf dem Windows- und dem Mac-Computer abgeschlossen haben, folgen Sie den Anweisungen in [Connecting to the Mac using XMA](http://developer.xamarin.com/guides/ios/getting_started/installation/windows/#Connecting_to_the_Mac_Using_XMA) (Anschließen an den Mac unter Verwendung von XMA) (xamarin.com), sodass Sie mit iOS und dem Mac in Visual Studio auf dem Windows-Computer arbeiten können.  
  
##  <a name="windows"></a> Windows-Setup innerhalb von Parallels (Visual Studio und Xamarin)  
  
1.  Auf dem Windows-Desktop, den Sie innerhalb von Parallels/VMWare konfiguriert haben, können Sie [das Installationsprogramm für eine beliebige Edition von Visual Studio 2015 herunterladen und starten](https://www.visualstudio.com/downloads/download-visual-studio-vs.aspx) (Community, Professional oder Enterprise). Visual Studio 2015 Community ist die kostenlose Edition; die Editionen Professional und Enterprise können als Testversion für 30 Tage verwendet werden.  
  
2.  Wählen Sie im Installationsprogramm eine **Benutzerdefinierte** Installation aus:  
  
     ![Auswählen der Option „Benutzerdefiniert“ bei Visual Studio-Installation](../cross-platform/media/cross-plat-xamarin-setup-1.png "Plattformübergreifendes Xamarin-Setup 1")  
  
3.  Aktivieren/deaktivieren Sie die folgenden Felder:  
  
    1.  Aktivieren Sie **Plattformübergreifende mobile Entwicklung > C#/.NET (Xamarin)**. Dadurch werden unter „Häufig verwendete Tools und Software Development Kits“ auch automatisch verschiedene Android-Tools ausgewählt.  
  
         ![Aktivieren Sie die Xamarin-Option unter „Plattformübergreifende mobile Entwicklung“](../cross-platform/media/cross-plat-xamarin-setup-2.png "Plattformübergreifendes Xamarin-Setup 2")  
  
    2.  Deaktivieren Sie **Plattformübergreifende mobile Entwicklung > Microsoft Visual Studio-Emulator für Android**.  
  
4.  Klicken Sie auf die Schaltfläche „Installieren“, und führen Sie den Vorgang aus. Dieser Vorgang nimmt ebenfalls einige Zeit in Anspruch. In der Zwischenzeit können Sie mit diesem Thema fortfahren und [Erfahren Sie mehr über die Entwicklung für mobile Plattformen mit Xamarin](../cross-platform/learn-about-mobile-development-with-xamarin.md) durcharbeiten.  
  
5.  Starten Sie Visual Studio nach dem Abschluss der Installation, und melden Sie sich mit Ihrem Microsoft-Konto an, wenn Sie dazu aufgefordert werden (es handelt sich um das gleiche Konto, das Sie für Windows verwenden). Suchen Sie anschließend mithilfe von **Extras > Optionen > Xamarin** oder **Extras > Optionen > Xamarin > Sonstige** nach Xamarin-Updates; dazu dient der Link **Jetzt überprüfen**:  
  
     ![Überprüfung auf Xamarin-Updates in den Visual Studio-Optionen](../cross-platform/media/cross-plat-xamarin-setup-3.png "Plattformübergreifendes Xmarin-Setup 3")  
  
    > [!NOTE]
    >  Aktualisieren Sie Xamarin auf Version 4.0.3.214 oder höher, um Probleme mit früheren Xamarin-Lizenzen zu vermeiden.  Wenn Sie Updates suchen und eine Fehlermeldung bezüglich Microsoft-Build-Tools sehen, lesen Sie den Thread in den [Xamarin-Foren](http://forums.xamarin.com/discussion/69015/xamarin-update-on-vs-2013-says-i-need-the-build-tools-for-vs-2015).
  
6.  Sobald Sie die Installation von Xamarin auf dem Windows- und dem Mac-Computer abgeschlossen haben, folgen Sie den Anweisungen in [Connecting to the Mac using XMA](http://developer.xamarin.com/guides/ios/getting_started/installation/windows/#Connecting_to_the_Mac_Using_XMA) (Verbinden mit dem Mac unter Verwendung von XMA) (xamarin.com), sodass Sie mit iOS in Visual Studio arbeiten können.  
  
##  <a name="verify"></a> Überprüfen der Umgebung  
 Nachdem die Installationsprogramme abgeschlossen wurden, sollten Sie ein paar Minuten investieren, um zu überprüfen, ob alles für den Einstieg in die Xamarin-Entwicklung bereit ist.  
  
### <a name="xamarin-studio"></a>Xamarin Studio  
 Stellen Sie beim Navigieren zu den bereitgestellten Links zunächst sicher, dass in der oberen rechten Ecke **Xamarin Studio** ausgewählt ist, sodass Ihnen die richtige Version der Xamarin-Dokumentation angezeigt wird:  
  
 ![Auswählen von Xamarin Studio, um die richtige Dokumentation auf Xamarin.com anzuzeigen](../cross-platform/media/crossplat-xamarin-mac-1.png "CrossPlat Xamarin Mac 1")  
  
 **Android**  
  
1. Überprüfen Sie das Erstellen eines Android-Projekts, indem Sie den Anweisungen unter [Create an Android Project](http://developer.xamarin.com/recipes/android/general/projects/create_an_android_project/) (xamarin.com) folgen.  
  
2. Überprüfen Sie das Debuggen im Android Player mithilfe von [Android Player > Integration with Xamarin Studio-Dokumentation](https://developer.xamarin.com/guides/android/getting_started/installation/android-player/#Integration_with_Xamarin_Studio) (xamarin.com).  
  
   **iOS**  
  
3. Überprüfen Sie das Erstellen eines iOS-Projekts, indem Sie den Anweisungen unter [Create an iOS Project](http://developer.xamarin.com/recipes/ios/general/projects/create_an_ios_project/) (xamarin.com) folgen.  
  
4. Überprüfen Sie das Debuggen im iOS-Simulator anhand der [Debugging in the Simulator-Dokumentation](https://developer.xamarin.com/guides/ios/deployment,_testing,_and_metrics/debugging_in_xamarin_ios/#Debugging_on_the_Simulator) (xamarin.com).  
  
### <a name="visual-studio"></a>Visual Studio  
 Stellen Sie beim Navigieren zu den bereitgestellten Links zunächst sicher, dass in der oberen rechten Ecke **Visual Studio** ausgewählt ist, sodass Ihnen die richtige Version der Xamarin-Dokumentation angezeigt wird:  
  
 ![Auswählen von Visual Studio, um die richtige Dokumentation auf Xamarin.com anzuzeigen](../cross-platform/media/crossplat-xamarin-mac-2.png "CrossPlat Xamarin Mac 2")  
  
 Melden Sie sich auch über **Extras > Xamarin-Konto...**  bei Ihrem Xamarin-Konto an.  
  
 **Android**  
  
1. Überprüfen Sie das Erstellen eines Android-Projekts, indem Sie den Anweisungen unter [Create an Android Project](http://developer.xamarin.com/recipes/android/general/projects/create_an_android_project/) (xamarin.com) folgen.  
  
2. Überprüfen Sie den Android-Designer: Öffnen Sie im Android-Projekt im Projektmappen-Explorer die Datei **Ressourcen > Layout > Main.axml**.  
  
   -   Wenn eine Fehlermeldung „Das installierte Android SDK ist veraltet“ angezeigt wird, klicken Sie in dieser Nachricht auf **Android SDK öffnen**, und wählen Sie die neueste verfügbare SDK-Version aus. Beachten Sie, dass Sie Visual Studio als Administrator ausführen müssen, um das SDK zu aktualisieren.  
  
3. Überprüfen Sie, ob Sie aus Visual Studio eine Verbindung zu dem Emulator herstellen können, der auf dem Mac installiert ist.  Das Ergebnis dieses Vorgangs ist, dass der Xamarin Player in der Liste der Emulatoren angezeigt wird, die in Visual Studio zum Debuggen ausgewählt werden können.  Folgen Sie hierzu den Anweisungen unter [Connecting Visual Studio to the Xamarin Android Player](http://developer.xamarin.com/guides/android/deployment,_testing,_and_metrics/android-player-with-visual-studio-in-vm/) (xamarin.com).  
  
   **iOS**  
  
4. Überprüfen Sie, ob der Mac im Netzwerk verfügbar und mit Visual Studio gepaart ist, wie unter [Connecting to the Mac using XMA](http://developer.xamarin.com/guides/ios/getting_started/installation/windows/#Connecting_to_the_Mac_Using_XMA) (xamarin.com) beschrieben.  
  
5. Überprüfen Sie das Erstellen eines iOS-Projekts, indem Sie den Anweisungen unter [Create an iOS Project](http://developer.xamarin.com/recipes/ios/general/projects/create_an_ios_project/) (xamarin.com) folgen.  
  
6. Überprüfen des Storyboard-Designers: Öffnen Sie im iOS-Projekt im Projektmappen-Explorer die Datei **MainStoryboard.storyboard** . Hier bildet Visual Studio den Host für den Designer, der remote auf dem Mac ausgeführt wird.  
  
7. Überprüfen von Erstellen und Debuggen:  
  
   1.  Klicken Sie mit der rechten Maustaste im Projektmappen-Explorer auf das iOS-Projekt, und wählen Sie **Als Startprojekt festlegen**aus.  
  
   2.  Wählen Sie in der Erstellen-Dropdownliste von Visual Studio das Ziel **iPhoneSimulator** aus, wie unten dargestellt. Wenn keine Simulatoren aufgelistet sind, starten Sie Xcode auf dem Mac, wählen Sie **Xcode->Einstellungen** aus, und klicken Sie auf **Laden**. Unter **Komponenten** sollten die für den Download verfügbaren Simulatorversionen zu sehen sein. Weitere Debuganweisungen finden Sie auf der Seite [Debugging](https://developer.xamarin.com/guides/ios/deployment,_testing,_and_metrics/debugging_in_xamarin_ios/#Debugging_on_the_Simulator) von Xamarin (xamarin.com).  
  
        ![Auswählen von iPhoneSimulator als Buildziel](../cross-platform/media/crossplat-xamarin-verify-5.png "CrossPlat Xamarin Verify 5")  
  
   3.  Wählen Sie in der Debug-Dropdownliste von Visual Studio ein iPhone-Ziel aus, und starten Sie den Debugger, indem Sie F5 drücken. Dadurch wird der Simulator auf dem Mac gestartet, auf dem Sie mit der App interagieren, während das Debuggen in Visual Studio erfolgt.  
  
        ![Auswählen eines iPhones als Debugziel](../cross-platform/media/crossplat-xamarin-verify-6.png "CrossPlat Xamarin Verify 6")
