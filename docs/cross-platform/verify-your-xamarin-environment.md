---
title: "&#220;berpr&#252;fen Ihrer Xamarin-Umgebung | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: fd39882e-06d1-4b39-80d2-4d07b6e4f8f5
caps.latest.revision: 13
caps.handback.revision: 7
ms.author: "crdun"
manager: "crdun"
---
# &#220;berpr&#252;fen Ihrer Xamarin-Umgebung
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Nachdem die Installationsprogramme abgeschlossen wurden \(siehe dazu [Setup und Installation](../cross-platform/setup-and-install.md)\) sollten Sie ein paar Minuten investieren, um zu überprüfen, ob alles für den Einstieg in die Xamarin\-Entwicklung bereit ist.  
  
## Alle Plattformen  
 Erstellen Sie in Visual Studio eine neue Xamarin\-Projektmappe mithilfe von **Datei \> Neues Projekt**, erweitern Sie im Dialogfeld **Vorlagen \> Andere Sprachen \> Visual C\# \> Plattformübergreifend**, wählen Sie **Leere App \(nativ portabel\)** aus, und klicken Sie auf „OK“. Dadurch wird eine Projektmappe mit einem Projekt der gemeinsamen portablen Klassenbibliothek und einzelnen Projekten für Android, iOS und Windows erstellt:  
  
 ![Ergebnisse der Erstellung eines neuen Projekts aus der Vorlage „Leere Anwendung &#40;systemeigen mobil&#41;“](../cross-platform/media/crossplat-xamarin-verify-1.png "CrossPlat Xamarin Verify 1")  
  
> [!NOTE]
>  Wenn die Vorlagen nicht vorhanden sind, lesen Sie [Fehlen die Xamarin-Projektvorlagen? Versuchen Sie Folgendes](#missing) am Ende dieser Seite.  
  
## Android  
  
1.  Überprüfen Sie den Android\-Designer: öffnen Sie im Projektmappen\-Explorer die Datei **Ressourcen \> Layout \> Main.axml**.  
  
    -   Wenn eine Fehlermeldung "Das installierte Android\-SDK ist veraltet" angezeigt wird, klicken Sie in dieser Nachricht auf **Android SDK öffnen**, und wählen Sie die neueste verfügbare SDK\-Version aus. Beachten Sie, dass Sie Visual Studio als Administrator ausführen müssen, um das SDK zu aktualisieren.  
  
2.  Überprüfen des Erstellens und des Debuggens im Emulator \(oder Gerät\):  
  
    -   Klicken Sie mit der rechten Maustaste im Projektmappen\-Explorer auf das Android\-Projekt, und wählen Sie **Als Startprojekt festlegen** aus.  
  
         ![Visual Studio&#45;Option „Als Startprojekt festlegen“](../cross-platform/media/crossplat-xamarin-verify-2.png "CrossPlat Xamarin Verify 2")  
  
    -   Wählen Sie entsprechend dem Betriebssystem einen Emulator aus. Ist ein Android\-Entwicklungsgerät an Ihren Computer angeschlossen, wird dieses Gerät hier zusammen mit den Emulatoren aufgelistet:  
  
        -   Windows 8\+: Wählen Sie in der Debug\-Dropdownliste ein **VS Emulator**\-Ziel aus, wie unten dargestellt, und starten Sie den Debugger durch Drücken von **F5**. Weitere Details finden Sie unter [Introducing Visual Studio’s Emulator for Android](http://blogs.msdn.com/b/visualstudioalm/archive/2014/11/12/introducing-visual-studio-s-emulator-for-android.aspx) \(Visual Studio ALM\-Blog\). Wenn bei der Inbetriebnahme des Emulators Probleme auftreten, finden Sie Hilfe unter [Fehlerbehebung beim Visual Studio\-Emulator für Android](../cross-platform/troubleshooting-the-visual-studio-emulator-for-android.md). Sie können auch neue Geräteprofile für den Emulator erstellen, indem Sie **Extras \> Visual Studio\-Emulator für Android...** auswählen.  
  
             ![Auswählen des Visual Studio&#45;Emulators für Android als Debugziel](../cross-platform/media/crossplat-xamarin-verify-3.png "CrossPlat Xamarin Verify 3")  
  
        -   Für Windows 7 und früher: wählen Sie stattdessen in der Dropdownliste den Xamarin Player für Android aus, und drücken Sie F5, um ihn auszuführen. Ausführliche Informationen über den Xamarin Player und dessen Geräte\-Manager sowie Tipps zur Fehlerbehebung finden Sie unter [Xamarin Android Player](http://developer.xamarin.com/guides/android/getting_started/installation/android-player/) \(xamarin.com\).  
  
> [!NOTE]
>  In Visual Studio sehen Sie möglicherweise das Symbol für den Android Emulator Manager \(AVD\) in der Symbolleiste \(siehe unten\), über das der Geräte\-Manager geöffnet wird, mit dem sich speziell der Google Android\-Emulator konfigurieren lässt.  Dieses Symbol bedingt keine Auswirkungen auf den Visual Studio\-Emulator für Android oder den Xamarin Player, die jeweils ihren eigenen Geräte\-Manager zum Konfigurieren von Profilen haben.  Weitere Details finden Sie unter [Introducing Visual Studio’s Emulator for Android](http://blogs.msdn.com/b/visualstudioalm/archive/2014/11/12/introducing-visual-studio-s-emulator-for-android.aspx) \(Visual Studio ALM\-Blog\) und unter [Xamarin Android Player](http://developer.xamarin.com/guides/android/getting_started/installation/android-player/) \(xamarin.com\).  
> ![CrossPlat Xamarin Verify 7](../cross-platform/media/crossplat-xamarin-verify-7.png "CrossPlat Xamarin Verify 7")  
  
## Windows Phone  
  
1.  Überprüfen des Windows Phone\-Designers: Öffnen Sie im Windows Phone\-Projekt im Projektmappen\-Explorer die Datei **MainPage.xaml**.  
  
2.  Überprüfen Sie das Erstellen und das Debuggen im Emulator oder auf einem Gerät \(Hinweis: dieser Schritt erfordert, dass der Windows Phone\-Emulator mithilfe von Visual Studio\-Setup installiert wurde oder ein verbundenes Gerät vorhanden ist\):  
  
    -   Klicken Sie mit der rechten Maustaste im Projektmappen\-Explorer auf das Windows Phone\-Projekt, und wählen Sie **Als Startprojekt festlegen** aus.  
  
    -   Wählen Sie in der Debug\-Dropdownliste von Visual Studio ein **Emulator 8.1**\-Ziel oder ein angeschlossenes Gerät aus, wie unten dargestellt, und starten Sie den Debugger durch Drücken von F5.  
  
         ![Auswählen eines Windows Phone&#45;Emulators als Debugziel](../cross-platform/media/crossplat-xamarin-verify-4.png "CrossPlat Xamarin Verify 4")  
  
    -   Wenn Sie beim Arbeiten mit dem Emulator auf Probleme stoßen, lesen Sie [Troubleshooting the Windows Phone 8 Emulator](https://msdn.microsoft.com/library/windows/apps/jj681694.aspx).  
  
## iOS  
  
1.  Überprüfen Sie, ob der Mac im Netzwerk verfügbar und mit Visual Studio gepaart ist, wie unter [Connecting to the Mac](http://developer.xamarin.com/guides/ios/getting_started/installation/windows/xamarin-mac-agent/) \(xamarin.com\) beschrieben.  
  
2.  Überprüfen des Storyboard\-Designers: Öffnen Sie im iOS\-Projekt im Projektmappen\-Explorer die Datei **Main.storyboard**. Hier bildet Visual Studio den Host für den Designer, der remote auf dem Mac ausgeführt wird.  
  
3.  Überprüfen von Erstellen und Debuggen:  
  
    1.  Klicken Sie mit der rechten Maustaste im Projektmappen\-Explorer auf das iOS\-Projekt, und wählen Sie **Als Startprojekt festlegen** aus.  
  
    2.  Wählen Sie in der Erstellen\-Dropdownliste von Visual Studio das Ziel **iPhoneSimulator** \(siehe unten\) oder das Ziel **iPhone** aus, wenn Sie ein verbundenes Gerät haben. Wenn keine Simulatoren aufgelistet sind, starten Sie Xcode auf dem Mac, wählen Sie **Xcode\-\>Preferences** aus, und klicken Sie auf **Laden**. Unter **Komponenten** sollten die für den Download verfügbaren Simulatorversionen zu sehen sein. Weitere Debuganweisungen finden Sie auf der Seite [Debugging](https://developer.xamarin.com/guides/ios/deployment,_testing,_and_metrics/debugging_in_xamarin_ios/#Debugging_on_the_Simulator) von Xamarin \(xamarin.com\).  
  
         ![Auswählen des iPhoneSimulator&#45;Buildziels](../cross-platform/media/crossplat-xamarin-verify-5.png "CrossPlat Xamarin Verify 5")  
  
    3.  Wählen Sie in der Debug\-Dropdownliste von Visual Studio ein iPhone\-Ziel aus, und starten Sie den Debugger, indem Sie F5 drücken. Dadurch wird der Simulator auf dem Mac gestartet, auf dem Sie mit der App interagieren, während das Debuggen in Visual Studio erfolgt. Wenn Sie mit einem physischen iPhone oder iPad arbeiten, das mit dem Mac verbunden ist, wird es hier angezeigt, und Sie können es stattdessen auswählen. Wenn keine Geräte oder Simulatoren aufgelistet werden, überprüfen Sie die Verbindung zum Mac. Lesen Sie dazu das in Schritt 1 oben verknüpfte Thema durch, oder navigieren Sie zu **Extras** \> **iOS** \> **Xamarin Mac Agent**  
  
         ![Auswählen eines iPhone&#45;Debugziels](../cross-platform/media/crossplat-xamarin-verify-6.png "CrossPlat Xamarin Verify 6")  
  
    4.  Gibt es Probleme beim Herstellen einer Verbindung mit dem Mac, lesen [Connection Troubleshooting](http://developer.xamarin.com/guides/ios/getting_started/installation/windows/xamarin-mac-agent/xma-troubleshooting/) \(xamarin.com\).  
  
    5.  Wird die Fehlermeldung „No installed provisioning profiles match the installed iOS signing keys“ angezeigt, gehen Sie wie folgt vor:  
  
        -   Vergewissern Sie sich, dass Ihr Apple ID\-Konto in Xcode auf dem Mac hinzugefügt wurde, wie dies unter [Adding Your Account to Xcode](https://developer.apple.com/library/ios/documentation/IDEs/Conceptual/AppStoreDistributionTutorial/AddingYourAccounttoXcode/AddingYourAccounttoXcode.html) \(apple.com\) beschrieben ist.  Nachdem Ihr Konto hinzugefügt wurde, müssen Sie sowohl Visual Studio als auch Xcode neu starten.  
  
             ![CrossPlat Xamarin Verify 8](../cross-platform/media/crossplat-xamarin-verify-8.png "CrossPlat Xamarin Verify 8")  
  
        -   Stellen Sie sicher, dass in den iOS\-Projekteigenschaften auf der Registerkarte „iOS Bundle Signing“ das Feld „Custom entitlement“ für die aktive Debugkonfiguration leer ist.  Hinweis: Sie sollten nur dann versuchen, diese Einstellung zu löschen, wenn die oben genannte Fehlermeldung angezeigt wurde.  
  
##  <a name="missing"></a> Fehlen die Xamarin\-Projektvorlagen? Versuchen Sie Folgendes  
 Wenn Sie Xamarin direkt von der Xamarin\-Website installieren und Visual Studio 2013 und Visual Studio 2015 parallel installiert sind, fehlen möglicherweise die Vorlagen. Das lässt sich allerdings leicht beheben: Aktivieren Sie einfach im Xamarin\-Setupprogramm die Funktion **Xamarin für Visual Studio 2015**.  
  
1.  Öffnen Sie in der Systemsteuerung **Programme und Features**, wählen Sie das **Xamarin**\-Element aus, und klicken Sie auf **Ändern**.  
  
2.  Klicken Sie im Setup\-Assistenten von Xamarin, der dann angezeigt wird, auf **Weiter** und dann auf **Ändern**.  
  
3.  Erweitern Sie in der Liste der optional zu installierenden Features **Xamarin für Visual Studio 2015**, wählen Sie **wird auf dem lokalen Laufwerk installiert** aus, und klicken Sie auf **Weiter**, um mit dem Hinzufügen des Features fortzufahren.