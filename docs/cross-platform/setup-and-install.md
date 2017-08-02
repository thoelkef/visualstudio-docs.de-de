---
title: Setup und Installation | Microsoft-Dokumentation
ms.custom: 
ms.date: 04/13/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2cfcad00-352c-4161-814c-f5ae32d8ada8
caps.latest.revision: 16
author: ghogen
ms.author: ghogen
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Human Translation
ms.sourcegitcommit: 47057e9611b824c17077b9127f8d2f8b192d6eb8
ms.openlocfilehash: d353d8a0a41ad487191b79aa68f26585cf9902b4
ms.contentlocale: de-de
ms.lasthandoff: 05/13/2017

---
# <a name="setup-and-install"></a>Setup und Installation
Zum Erstellen von systemeigenen iOS- Android- und Windows-Apps aus einer gemeinsamen C#/.NET-Codebasis mithilfe von Xamarin benötigen Sie die folgenden Komponenten:  
  
-   Für das Arbeiten mit Windows- und Android-Apps: einen Windows-Entwicklungscomputer mit installiertem Visual Studio 2017 oder Visual Studio 2015 und Xamarin. Sie können auch Visual Studio 2013 anhand der Anleitungen für die [direkte Installation von Xamarin](https://developer.xamarin.com/guides/cross-platform/getting_started/requirements/#install) (xamarin.com) verwenden. 
  
-   Für das Arbeiten mit iOS-Apps: einen Mac mit installiertem macOS Sierra 10.12 oder höher, XCode und Xamarin.  
  
 Sie können die Windows- und Mac-Computer gleichzeitig einrichten, und während die Installationsprogramme ausgeführt werden, können Sie in [Erfahren Sie mehr über die Entwicklung für mobile Plattformen mit Xamarin](../cross-platform/learn-about-mobile-development-with-xamarin.md) das erforderliche Hintergrundmaterial durchlesen und ansehen.  
 
Wenn Sie nach dem Setup und der Installation Probleme mit der Verwendung von Xamarin haben, posten Sie Ihre Frage auf [forums.xamarin.com](http://forums.xamarin.com/).
  
> [!NOTE]
>  Seit dem 31. März 2016 ist Xamarin ohne zusätzliche Kosten im Lieferumfang aller Editionen von Visual Studio enthalten. Eine separate Lizenz ist nicht erforderlich. Xamarin Studio Community für Mac ist auch für Studenten, OSS-Entwickler und kleine Teams kostenlos. Beachten Sie, dass Sie für vorhandene Installationen von Visual Studio, die mit früheren Xamarin-Lizenzen konfiguriert sind, Xamarin auf Version 4.0.3.214 oder höher aktualisieren müssen. Informationen hierzu finden Sie unter **Extras > Optionen > Xamarin > Sonstige**, klicken Sie auf **Jetzt prüfen**, und laden Sie das Update 4.0.3.214 herunter. Wenn Sie Visual Studio neu starten, wechseln Sie zu **Extras > Xamarin-Konto...**. Dort sollten Sie den aktualisierten Status sehen.  
  
##  <a name="prereq"></a> Voraussetzungen  
  
###  <a name="for-targeting-windows-and-android"></a>Für Windows und Android 
  
1.  Empfohlen: physischer Windows-Computer (keine VM) unter Windows 8 oder höher zum Erzielen einer optimalen Android-Emulatorleistung. (Haben wir erwähnt, dass Sie einen physischen Computer benötigen anstelle einer VM?)  
  
2.  Sie können einen Computer mit Windows 7 oder früher verwenden. In diesem Fall müssen Sie jedoch den Xamarin Player für Android als Emulator verwenden. 
    
3. Bei beiden Konfigurationen können Sie Apps immer direkt auf verbundenen physischen Geräten ausführen.  
  
### <a name="for-targeting-ios"></a>Für iOS  
  
1.  Einen vernetzten Mac oder Mac mini mit macOS Sierra unter macOS 10.12 oder höher (für Xcode 8.3 erforderlich).  
  
2.  Bei Verwendung von Visual Studio auf einem Windows-Computer (7 und höher) als primäre Entwicklungsumgebung ist ein vernetzter Mac nur zum Kompilieren und Debuggen von iOS-Apps, Anschließen an den iOS-Simulator oder verbundene Geräte und Verwenden des Storyboard-Designers in Visual Studio für das Design der Benutzeroberfläche. Ältere Mac-Modelle sind für diese sekundäre Rolle völlig ausreichend.  
  
##  <a name="windows"></a> Windows-Setup (Visual Studio und Xamarin)  
  
> [!TIP]
>  Diese Anweisungen gelten für Visual Studio 2017. Anweisungen für Visual Studio 2015 finden Sie auf [MSDN](https://msdn.microsoft.com/en-us/library/mt613162.aspx). Um Xamarin mit Visual Studio 2013 (Update 2 erforderlich ist) zu verwenden, führen Sie die Schritte für die [direkte Installation von Xamarin](https://developer.xamarin.com/guides/cross-platform/getting_started/requirements/#install) (xamarin.com) aus.  
  
1.  [Laden Sie das Installationsprogramm für eine beliebige Edition von Visual Studio 2017 herunter, und führen Sie es aus](https://www.visualstudio.com/downloads/) (Community, Professional oder Enterprise). Visual Studio 2017 Community ist die kostenlose Edition. Die Editionen Professional und Enterprise können zu Testzwecken nach Kauf einer Lizenz 30 Tage verwendet werden.  
  
    1.  Wenn Sie Visual Studio 2017 bereits installiert haben, führen Sie den **Visual Studio-Installer** über das **Startmenü** aus.
  
2.  Klicken Sie im Installationsprogramm _neben_ **Starten** auf die Schaltfläche **Zusätzliche Optionen** (Drei-Balken-Symbol), und wählen Sie dann **Ändern**:  
  
     ![Auswählen der Option „Ändern“ bei Visual Studio-Installation](~/docs/cross-platform/media/cross-plat-xamarin-setup-1a.png "Plattformübergreifendes Xamarin-Setup 1")  
  
3.  Aktivieren Sie die folgenden Felder:  
  
    1.  **Mobil und Gaming > Mobile Entwicklung mit .NET**. Dadurch werden unter „Häufig verwendete Tools und Software Development Kits“ auch automatisch verschiedene Android-Tools ausgewählt. Diese Option sollte auch alle vorhandenen Xamarin-Installationen aktualisieren.  
  
         ![Aktivieren der Option „Mobile Entwicklung“ unter „Spiele und mobile Entwicklung“](~/docs/cross-platform/media/cross-plat-xamarin-setup-2a.png "Plattformübergreifendes Xamarin-Setup 2")  
  
    2. (Optional) **Windows > Entwicklung für die universelle Windows-Plattform**. Hier finden Sie Optionen zum Installieren von Emulatorimages, deren Download längere Zeit beansprucht; Sie können auch später jederzeit zum Visual Studio-Installationsprogramm zurückkehren, um sie hinzuzufügen. 
  
4.  Klicken Sie auf die Schaltfläche **Ändern**, und führen Sie den Vorgang aus. Dieser Vorgang nimmt ebenfalls einige Zeit in Anspruch. In der Zwischenzeit können Sie mit den Anweisungen zum Mac-Setup fortfahren oder [Erfahren Sie mehr über die Entwicklung für mobile Plattformen mit Xamarin](../cross-platform/learn-about-mobile-development-with-xamarin.md) durcharbeiten.  
  
5.  Starten Sie Visual Studio nach dem Abschluss der Installation, und melden Sie sich mit Ihrem Microsoft-Konto an, wenn Sie dazu aufgefordert werden (es handelt sich um das gleiche Konto, das Sie für Windows verwenden).  
      
6.  Verwenden Sie zum Testen von Android-Apps den [Android SDK-Emulator](https://developer.xamarin.com/guides/android/deployment,_testing,_and_metrics/debug-on-emulator/android-sdk-emulator/), sofern Sie keine physischen Geräte haben. Siehe den Hinweis unten.  
  
 **Hinweis zu Emulatoren auf Windows-Computern:** Da die CPUs jeweils nur eine Virtualisierungstechnologie unterstützen, sollte auf einem Entwicklungscomputer jeweils nur eine eingesetzt werden. Die drei wichtigsten Virtualisierungstechnologien sind Hyper-V (das vom Visual Studio Emulator für Android und dem Windows Phone-Emulator verwendet wird), Virtual Box (das von Genymotion verwendet wird) und Intel HAXM (das vom Android SDK-Emulator verwendet wird). Aufgrund von verschiedenen Problemen zwischen Hyper-V und Virtual Box sollten auf einem Computer jeweils nur Emulatoren eines dieser Typen verwendet werden; darauf beziehen sich auch die oben genannten Empfehlungen für den Einsatz von Hyper-V auf Computern mit Windows 8 und höher und Intel HAXM-Emulatoren auf Windows 7 sowie bei der Ausführung von Windows auf einem Mac.  
  
##  <a name="mac"></a> Mac-Setup (Apple ID, Xcode und Xamarin)  
  
1.  Erstellen Sie eine kostenlose Apple-ID unter [https://appleid.apple.com](https://appleid.apple.com/), wenn Sie noch keine besitzen. Dies ist für die Installation von und die Anmeldung bei Xcode erforderlich.  
  
2.  Laden Sie Xcode von  [https://developer.apple.com/xcode/](https://developer.apple.com/xcode/)herunter, installieren Sie Xcode, und fügen Sie Ihre Apple ID so hinzu, wie dies unter [Adding Your Account to Xcode](https://developer.apple.com/library/content/documentation/IDEs/Conceptual/AppStoreDistributionTutorial/AddingYourAccounttoXcode/AddingYourAccounttoXcode.html#//apple_ref/doc/uid/TP40013839-CH40-SW1) (apple.com) beschrieben ist.  
  
3.  Laden Sie Xamarin herunter, und installieren Sie es, indem Sie die Anweisungen unter [Installing and Configuring Xamarin.iOS](http://developer.xamarin.com/guides/ios/getting_started/installation/mac/) (xamarin.com) befolgen.  
  
4.  Sobald Sie die Installation von Xamarin auf dem Windows- und dem Mac-Computer abgeschlossen haben, folgen Sie den Anweisungen unter [Connecting to the Mac (Anschließen an den Mac)](http://developer.xamarin.com/guides/ios/getting_started/installation/windows/xamarin-mac-agent/) (xamarin.com), sodass Sie mit iOS und dem Mac in Visual Studio auf dem Windows-Computer arbeiten können.  
  
     Beide Computer müssen sich im selben lokalen Netzwerk befinden.
