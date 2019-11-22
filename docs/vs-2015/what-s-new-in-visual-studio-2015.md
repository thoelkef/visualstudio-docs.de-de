---
title: Neuerungen in Visual Studio 2015 | Microsoft-Dokumentation
titleSuffix: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.topic: conceptual
f1_keywords:
- VS.StartPage.WhatsNew
helpviewer_keywords:
- Visual Studio, what's new
- what's new [Visual Studio]
ms.assetid: 7307e180-ba28-4774-8a43-cbb980085a71
caps.latest.revision: 364
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 036ad2171c3b117049635247a980cd0f8411d887
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/21/2019
ms.locfileid: "74297562"
---
# <a name="what39s-new-in-visual-studio-2015"></a>Neuerungen in Visual Studio 2015
[!INCLUDE[vs2017banner](./includes/vs2017banner.md)]

Willkommen bei Visual Studio 2015, einer integrierten Suite von Entwicklerproduktivitätstools, Cloud-Diensten und Erweiterungen, mit denen Sie und Ihr Team großartige Apps und Spiele für das Web, den Windows Store, den Desktop, Android und iOS erstellen können.

Auf dieser Seite werden einige der wichtigsten Features beleuchtet, die seit Visual Studio 2013 RTM neu sind oder in einem der Updates für Visual Studio 2013 eingeführt wurden. Eine vollständige Liste der Neuerungen in Visual Studio 2015 finden Sie in den [Versionshinweisen](https://www.visualstudio.com/news/vs2015-vs).

To find out more about the many improvements and new features in Visual Studio ALM, see [What's new for TFS 2015](/tfs/server/whats-new?view=vsts#tfs-2015-rtm).

## <a name="a-new-setup-experience"></a>Ein neues Setuperlebnis
 [!INCLUDE[downloadvs](./includes/downloadvs-md.md)]

 Das neue Visual Studio-2015-Setuperlebnis wurde in Komponenten gegliedert, sodass Sie nur die erforderlichen Teile installieren müssen. Dadurch wurde die Installation für viele häufige Szenarien beschleunigt, dazu gehören auch die .NET- oder Webentwicklung. Wenn Sie andere Entwicklungsszenarien einsetzen, wie die plattformübergreifende mobile Entwicklung, oder Sie in C++ oder F# arbeiten, wählen Sie bei der Installation **Benutzerdefiniert** und wählen Sie dann die Komponenten und SDKs von Drittanbietern, die Sie benötigen. Die benutzerdefinierten Komponenten können Sie auch später installieren. Wenn Sie beispielsweise einfache Installation auswählen und dann versuchen, ein neues C++-Projekt zu erstellen, werden Sie aufgefordert, die C++-Entwicklungstools herunterzuladen.

 ![Visual Studio 2015 Setup Dialog](./ide/media/vs2015-setup-screen.png "VS2015_Setup_screen")

## <a name="sign-in-across-multiple-accounts"></a>Anmelden mit mehreren Konten
 Die neue optimierte Anmeldung in Visual Studio 2015 vereinfacht den Zugriff auf Online-Ressourcen erheblich, auch wenn Sie mehrere Visual Studio-Konten verwenden. Nach der Anmeldung bei Visual Studio sind Sie automatisch bei allen Instanzen von Visual Studio 2015 und Blend auf Ihrem Computer angemeldet. Durch die Anmeldung wird automatisch mit dem Roaming Ihrer Einstellungen begonnen. In Visual Studio 2015 wird Ihr Konto von mehreren Features gemeinsam verwendet. Solange Sie über ein gutes Token verfügen, können Sie über **Team Explorer**auf Ihre Visual Studio Team Services-Konten und über Ihr Microsoft Azure-Abonnement in Server Explorer auf Ihre Ressourcen und Websites zugreifen. Außerdem sehen Sie Ihre Azure-Ressourcen im Dialogfeld "Neues Projekt" für Application Insights-Projekte, und Sie sehen Ihre Konten für Azure Mobile, Azure Storage, [Microsoft Office 365](https://msdn.microsoft.com/office/aa905340.aspx) und [Saleforce.com developer](https://developer.salesforce.com/) im neuen Dialogfeld **Verbundenen Dienst hinzufügen** .

 Sie können in Visual Studio mit mehreren Benutzerkonten arbeiten, indem Sie sie nach und nach oder über den neuen Konto-Manager hinzufügen. Danach können Sie bei der Herstellung einer Verbindung mit Diensten oder beim Zugriff auf Onlineressourcen zwischen diesen Konten wechseln. Die hinzugefügten Konten werden in Visual Studio gespeichert, sodass Sie sie in jeder Instanz von Visual Studio oder Blend verwenden können. Visual Studio nimmt außerdem ein Roaming der Kontenliste (ohne Ihre wertvollen Anmeldeinformationen) mit Ihrem Personalisierungskonto vor, sodass Sie auf einem anderen Gerät schnell mit einem dieser Konten arbeiten können. Selbstverständlich können Sie im Dialogfeld "Kontoeinstellungen" Konten jederzeit entfernen. Informationen zu den ersten Schritten finden Sie unter [Work with multiple user accounts](./ide/work-with-multiple-user-accounts.md).

 ![Account Manager](./ide/media/vs2015-accountmanager.gif "VS2015_AccountManager")

## <a name="choose-your-target-platforms"></a>Auswählen der Zielplattform(en)
 Visual Studio 2015 unterstützt die plattformübergreifende Entwicklung für mobile Geräte. Sie können Apps und Spiele für iOS, Android und Windows mit einer gemeinsamen Codebasis erstellen, und das alles innerhalb der Visual Studio-IDE. All diese neuen Projekttypen werden im Dialogfeld "Datei" > "Neues Projekt" angezeigt.

 Und natürlich ist die Unterstützung herkömmlicher Desktopanwendungen besser denn je, mit jeder Menge Verbesserungen für Sprachen, Bibliotheken und Tools.

### <a name="cross-platform-mobile-apps-in-c-with-xamarin-for-visual-studio"></a>Plattformübergreifende mobile Apps in C# mit Xamarin for Visual Studio
 Xamarin ist ein mobiles Framework zum Schreiben von Code in C#, der systemintern in die gesamten iOS- und Android-APIs gebunden wird. Microsoft hat bei der Veröffentlichung von Xamarin for Visual Studio eng mit Xamarin zusammengearbeitet, einer Erweiterung, mit der Sie Apps für Android, iOS und Windows Phone in einem einzigen Projekt mit freigegebenem Code entwickeln können. Mit Xamarin verwenden Sie eine Sprache und eine Codebasis mit minimaler Deltas zwischen den Plattformen.  Xamarin for Visual Studio wird in Visual Studio 2010 und höher unterstützt. Die Starter Edition von Xamarin ist in Visual Studio 2015 enthalten. To get started, see [Build apps with native UI using Xamarin in Visual Studio](./cross-platform/build-apps-with-native-ui-using-xamarin-in-visual-studio.md).

### <a name="cross-platform-mobile-apps-in-htmljavascript-with-apache-cordova"></a>Plattformübergreifende mobile Apps in HTML/JavaScript mit Apache Cordova
 Die Visual Studio-Tools für Apache Cordova sind das Ergebnis enger Zusammenarbeit zwischen Microsoft und der Open Source Apache Cordova-Community. Die Tools ermöglichen plattformübergreifende mobile Entwicklung mit HTML, CSS und JavaScript (oder Typescript). Sie können mit einer einzigen Codebasis für Android, iOS und Windows entwickeln und von der reichhaltigen Visual Studio-IDE mit JavaScript IntelliSense, dem DOM Explorer, der JavaScript-Konsole, Haltepunkten, Überwachungen, dem Lokalfenster, "Nur eigenen Code" und mehr profitieren.  Mit den Visual Studio-Tools für Apache Cordova erhalten Ihre Apps über Plug-Ins, die eine gemeinsame JavaScript-API bereitstellen, Zugriff auf systemeigene Gerätefunktionen auf allen Plattformen. To get started, see [Get Started with Visual Studio Tools for Apache Cordova](https://msdn.microsoft.com/library/db446f2c-6ba4-4c76-aac5-4c66f43b8c42).

### <a name="cross-platform-mobile-games-in-c-with-unity"></a>Plattformübergreifende mobile Spiele in C# mit Unity
 Unity ist eine häufig verwendete Plattform für die 2D- und 3D-Spielentwicklung auf mehreren Plattformen. Sie können ein Spiel in C# schreiben und es dann nativ unter Android, iOS, Windows Phone und vielen weiteren Plattformen ausführen. Die Visual Studio-Tools für Unity sind eine Erweiterung, die Unity mit der Visual Studio-IDE integrieren. Mit dieser Erweiterung erhalten Sie zusätzlich zu allen Features der IDE und des Debuggers von Visual Studio Produktivitätsfeatures, die auf Unity-Entwickler ausgerichtet sind. Visual Studio-Tools für Unity Preview 2.0 sorgt neben einer Reihe neuer Features wie besserer Visualisierung von Objekten in den Fenstern "Lokal" und "Überwachen" zusätzlich für Unterstützung von Visual Studio 2015. Microsoft hat kürzlich SyntaxTree, den Ersteller der Visual Studio-Tools für Unity übernommen. Weitere Informationen zu Visual Studio-Tools für Unity und den Download der Visual Studio-Tools für Unity 2.0 Preview 2 finden Sie unter [Visual Studio-Tools für Unity 2.0](https://aka.ms/vstu).

### <a name="cross-platform-apps-and-libraries-for-native-c"></a>Plattformübergreifende Apps und Bibliotheken für systemeigenes C++
 C++ ist eine Sprache, die systemintern auf den meisten mobilen Geräten verfügbar ist. Sie können Sie verwenden, um plattformübergreifend gemeinsam genutzte Codebibliotheken zu schreiben, die für mehrere mobile Plattformen entwickelt werden können. Sie können sogar komplette mobile Apps in C++ erstellen. Mit Visual C++ erhalten Sie die Tools an die Hand, um plattformübergreifenden Code zu bearbeiten, zu erstellen, bereitzustellen und zu debuggen. Zusätzlich zu den Vorlagen für Windows-Apps können Sie Projekte aus Vorlagen für systemeigene Android Aktivitäts-Apps, iOS-Apps oder freigegebene Code-Bibliotheksprojekte für mehrere Plattformen erstellen, die hybride Xamarin-Apps enthalten. Mit dem plattformspezifischen IntelliSense können Sie APIs entdecken und Code für Android-, iOS- oder Windows-Ziele generieren. Sie können Ihr Build für x86- oder ARM-Plattformen konfigurieren und Ihren Code für den iOS-Simulator oder für an einen in das Netzwerk eingebundenen Mac angeschlossene iOS-Geräte und direkt angeschlossene Android-Geräte bereitstellen, oder Sie können zu Testzwecken den leistungsfähigen Microsoft Visual Studio-Emulator für Android verwenden. Im Visual Studio-Debugger können Sie Haltepunkte setzen, Variablen überwachen, den Stapel anzeigen und C++-Code schrittweise durchlaufen. Sie können abgesehen vom plattformspezifischsten Code den Code für mehrere App-Plattformen freigeben und eine Lösung für alle Plattformen in Visual Studio schreiben.

 To get started on cross-platform C++, see [Build cross-platform mobile apps with Visual C++](./misc/build-cross-platform-mobile-apps-with-visual-cpp.md)

### <a name="universal-windows-apps-for-any-windows-10-device"></a>Universelle Windows-Apps für Windows 10 Geräte
 Mit der universellen Windows-Plattform und unserem zentralen Windows-Kern können Sie die gleiche App auf jedem Windows 10-Gerät ausführen, von Smartphones bis zu Desktop-PCs. Erstellen Sie diese universellen Windows-Apps mit Visual Studio 2015 und den universellen Windows-App-Entwicklungstools.

 ![Universal Windows Platform](./cross-platform/media/uwp-coreextensions.png "UWP_CoreExtensions")

 Führen Sie Ihre App auf einem Windows 10-Phone, Windows 10-Desktop oder einer Xbox aus. Es ist das gleiche App-Paket. Mit der Einführung eines einzelnen, einheitlichen Windows 10-Kerns kann ein App-Paket auf allen Plattformen ausgeführt werden. Mehrere Plattformen verfügen über Erweiterungs-SDKs, die Sie zu Ihrer App hinzufügen können, um die Vorteile bestimmter plattformspezifischer Verhaltensweisen zu nutzen. Mit dem Erweiterungs-SDK für Mobilgeräte wird z. B. die auf einem Windows Phone gedrückte ZURÜCK-Taste behandelt. Wenn Sie in Ihrem Projekt auf ein Erweiterungs-SDK verweisen, fügen Sie einfach Laufzeitüberprüfungen hinzu, um zu prüfen, ob dieses SDK für diese Plattform verfügbar ist. Auf dieses Weise können Sie das gleiche App-Paket für alle Plattformen verwenden.

 Verwenden von C#, Visual Basic, C++ oder JavaScript zum Erstellen von [universellen Windows-Apps](https://msdn.microsoft.com/library/dn975273.aspx).

### <a name="web"></a>Web
 ASP.NET 5 ist ein wichtiges Update für MVC, WebAPI und SignalR und kann unter Windows, Mac und Linux ausgeführt werden.  ASP.NET 5 wurde von Grund auf als effizienter, zusammensetzbarer .NET-Stapel zum Erstellen moderner, cloudbasierter Apps entwickelt. Die Tools von Visual Studio 2015  sind enger in gängige Webentwicklungstools wie Bower und Grunt integriert. Informationen zu den ersten Schritten finden Sie in den zahlreichen Blogbeiträgen im  [Blog zu .NET-Webentwicklung und Tools](https://devblogs.microsoft.com/aspnet/).

### <a name="classic-desktop-and-windows-store"></a>Klassischer Desktop und Windows Store
 Visual Studio 2015 unterstützt auch weiterhin die Entwicklung für den klassischen Desktop und den Windows Store. Visual Studio wird parallel zu Windows stetig weiterentwickelt.  In Visual Studio 2015 haben die Bibliotheken und Sprachen für .NET sowie für C++ wesentliche Verbesserungen erfahren, die in allen Versionen von Windows verfügbar sind.

#### <a name="the-net-framework"></a>.NET Framework
 Microsoft [!INCLUDE[net_v46](./includes/net-v46-md.md)] bietet etwa 150 neue und 50 aktualisierte APIs, die mehr Szenarien ermöglichen. Mehr Auflistungen implementieren jetzt beispielsweise <xref:System.Collections.Generic.IReadOnlyCollection%601>, sodass sie einfacher zu verwenden sind. Darüber hinaus verfügt das zuvor erwähnte ASP.NET 5 über eine schlanke .NET-Plattform zum Erstellen moderner, cloudbasierter Apps.

 In C# für das .NET Framework geschriebene Windows Store-Apps können jetzt .NET Native nutzen, womit Apps in systemeigenen Code anstatt in eine Zwischensprache (Intermediate Language, IL) kompiliert werden. [!INCLUDE[net_v46](./includes/net-v46-md.md)] verfügt zudem über RyuJIT, einen 64-Bit-Just-In-Time (JIT)-Compiler.

 Die neuen C#- und VB-Compiler ("Roslyn") verkürzen die Kompilierzeiten erheblich und stellen umfassende Codeanalyse-APIs bereit. Visual Studio 2015 nutzt Roslyn für mehr Umgestaltungsmöglichkeiten einschließlich Umbenennen, Analyzern und schnellen Lösungen.

 Die Sprachen C# und Visual Basic enthalten zahlreiche kleinere Verbesserungen in der Unterstützung der Kernsprache und der IDE. Dank all dieser Verbesserungen wird die .NET-Codierung intuitiver, komfortabler und produktiver.

 For more information, see [What's New](https://msdn.microsoft.com/library/1d971dd7-10fc-4692-8dac-30ca308fc0fa) and the [.NET Blog](https://devblogs.microsoft.com/dotnet/).

#### <a name="c"></a>C++
 Visual C++ bietet erhebliche Verbesserungen in puncto Konformität mit der Sprache C++11/14, Unterstützung der plattformübergreifenden Entwicklung für mobile Geräte, Unterstützung für fortsetzbare Funktionen und Awaits (derzeit geplant für die Standardisierung in C++17), Verbesserungen und Fehlerbehebungen in den Implementierungen der C-Laufzeitbibliothek (CRT) und der C++-Standardbibliothek (STL), neue Compileroptimierungen, bessere Buildleistung, neue Diagnosefunktionen und neue Produktivitätstools im Code-Editor.

 For more information, see [What's New for Visual C++](https://msdn.microsoft.com/library/1cc09fad-85a2-43c2-b022-bb99f5fe0ad7) and the [Visual C++ Blog](https://devblogs.microsoft.com/cppblog/).

## <a name="device-preview-menu-bar"></a>Menü „Gerätevorschau“
 In universellen Windows-Plattformprojekten können Sie mit der Menüleiste „Gerätevorschau“ sehen, wie Ihre XAML-basierte Benutzeroberfläche auf verschiedenen Bildschirmgrößen gerendert wird.

 ![Device Preview menu](./ide/media/vs2015-device-preview.png "vs2015_device_preview")

## <a name="visual-studio-graphics-diagnostics"></a>Visual Studio-Grafikdiagnose
 Seit Visual Studio 2013 wurden zu der Visual Studio-Grafikdiagnose viele neue Features hinzugefügt, einschließlich der Frame-Analyse, Windows Phone-Unterstützung, der Funktion zum Bearbeiten und Anwenden im Shader sowie der Erfassungstools für die Befehlszeile. Es wurde auch die Unterstützung für das Debuggen von DirectX12 Apps hinzugefügt. Weitere Informationen finden Sie unter [Visual Studio-Grafikdiagnose](./debugger/visual-studio-graphics-diagnostics.md).

## <a name="connect-to-services"></a>Verbinden mit Diensten
 Mit Visual Studio 2015 ist es einfacher denn je, Ihre App mit Diensten zu verbinden.  Der neue Assistent zum Hinzufügen eines verbundenen Diensts konfiguriert Ihr Projekt, fügt die nötige Unterstützung für die Authentifizierung hinzu und lädt die nötigen NuGet-Pakete herunter, damit Sie schnell und einfach mit der Programmierung für Ihren Dienst beginnen können. Außerdem ist der Assistent zum Hinzufügen eines verbundenen Diensts in den neuen Konto-Manager integriert, um die Verwendung mehrerer Benutzerkonten und Abonnements zu erleichtern. Bei Visual Studio 2015 ist die Unterstützung der folgenden Dienste standardmäßig direkt enthalten (sofern Sie ein Konto besitzen):

1. Azure-Mobile Services

2. Azure Storage

3. Office 365 (E-Mail, Kontakte, Kalender, Dateien, Benutzer und Gruppen)

4. Salesforce

   Es werden ständig weitere Dienste hinzugefügt. Sie können sie entdecken, indem Sie im Assistenten auf den Link zum Suchen nach neuen Diensten klicken.

   ![Add Connected Services Dialog](./ide/media/vs2015-addconnectedservicedialog.png "VS2015_AddConnectedServiceDialog")

## <a name="design-your-ui"></a>Entwerfen der Benutzeroberfläche
 Die Blend-Umgebung zum Entwerfen von XAML-Benutzeroberflächen wurde wesentlich verbessert. Blend wurde völlig umgestaltet und bietet nun eine intuitivere Benutzeroberfläche, leistungsstärkere XAML-Bearbeitungsfunktionen, einschließlich IntelliSense, und bessere Integration in Visual Studio. Weitere Informationen finden Sie unter [Entwerfen von XAML-Code in Visual Studio](./designers/designing-xaml-in-visual-studio.md).

## <a name="cross-platform-debugging-support"></a>Unterstützung für plattformübergreifendes Debugging
 Mit Visual Studio können Sie systemeigene mobile Apps erstellen und debuggen, die auf Windows-, IOS- und Android-Geräten ausgeführt werden. Verwenden Sie den [Visual Studio Emulator für Android](https://devblogs.microsoft.com/devops/introducing-visual-studios-emulator-for-android/), oder schließen Sie ein Gerät an, und debuggen Sie Ihren Code direkt in Visual Studio.

- **JavaScript/Cordova**. Verwenden Sie die [Visual Studio-Tools für Apache Cordova](https://msdn.microsoft.com/library/dn879821\(v=vs.140\).aspx) , um systemeigene Apps für Windows, iOS und Android mit JavaScript zu erstellen.

     [Debug Your App](https://msdn.microsoft.com/library/c2a4a1d4-a4e8-47ec-811f-ad207c54f4d1) in the MSDN Library is a detailed look at Visual Studio debugging support for Cordova.

- **C#/Xamarin**. Verwenden Sie [Xamarin](https://msdn.microsoft.com/library/dn879698\(v=vs.140\).aspx) , um systemeigene Apps für Windows, iOS und Android in Visual Studio mit C# zu erstellen.

     [Debugging](https://docs.microsoft.com/xamarin/ios/deploy-test/debugging-in-xamarin-ios?tabs=windows) (iOS) und [Debug on Device](https://docs.microsoft.com/xamarin/android/deploy-test/debugging/debug-on-device?tabs=windows) in den [Xamarin-Entwicklerhandbüchern](https://docs.microsoft.com/xamarin/) beschreiben den Debugvorgang.

- **C++/Android**. Verwenden Sie die [Visual C++ for Cross-Platform Mobile Development](cross-platform/visual-cpp-for-cross-platform-mobile-development.md) -Vorlagen zusammen mit Drittanbietertools wie [Android NDK](https://developer.android.com/tools/sdk/ndk/index.html) zum Erstellen von systemeigenen Apps für Windows und Android.

## <a name="debugging-and-diagnostics"></a>Debuggen und Diagnose

For information about what’s new in diagnostics, see [What's New in Profiling Tools](./profiling/what-s-new-in-profiling-tools.md).

Im Folgenden werden neue oder verbesserte Tools vorgestellt, mit denen verschiedene Arten von Diagnosen und Analysen des Codes durchgeführt werden können:

### <a name="perftips"></a>PerfTips
 PerfTips zeigen beim Debuggen die Ausführungszeit von Methoden an, sodass Sie schnell Engpässe erkennen können, ohne den Profiler zu starten. Informationen zu den ersten Schritten finden Sie unter [PerfTips: Informationen zur Leistung auf einen Blick beim Debuggen mit Visual Studio](https://devblogs.microsoft.com/devops/perftips-performance-information-at-a-glance-while-debugging-with-visual-studio/)

### <a name="error-list"></a>Fehlerliste
 Die Fehlerliste kann nun nach einer beliebigen Spalte gefiltert werden. Sie zeigt zudem eine Liveansicht von Fehlern, Warnungen und Codeanalysen für die gesamte C#- oder Visual Basic-Projektmappe an, selbst wenn eine Codeänderung Tausende von Warnungen nach sich zieht. Die neue Fehlerliste ist abwärtskompatibel zur derzeitigen Verwendung. Weitere Informationen finden Sie unter [Error List Window](./ide/reference/error-list-window.md).

### <a name="gpu-usage-tool"></a>GPU-Auslastungstool
 Das GPU-Auslastungstool hilft Ihnen dabei, GPU-Auslastungsdaten in DirectX-Apps und Spielen zu sammeln und zu analysieren. Und Sie können ermitteln, ob Leistungsengpässe in der CPU oder GPU entstehen. Informationen zu den ersten Schritten mit dem Tool finden Sie im [Blogbeitrag des Visual C++-Teams](https://devblogs.microsoft.com/cppblog/gpu-usage-tool-in-visual-studio-2013-update-4-ctp1/).

## <a name="live-code-analysis-light-bulbs"></a>Livecodeanalyse (Glühbirnen)
 Der neue Roslyn-Compiler für C# und Visual Basic ermöglicht nicht nur kürzere Kompilierzeiten, sondern auch völlig neue Szenarien wie eine Livecodeanalyse, die schon bei der Eingabe umfassendes und anpassbares Feedback und Vorschläge im Code-Editor bieten. In Visual Studio 2015 werden am linken Rand Glühbirnen (bei Verwendung der Tastatur) oder eine QuickInfo (beim Zeigen auf einen Fehler mit der Maus) angezeigt. Die Glühbirne zeigt in Echtzeit an, dass der Compiler (möglicherweise mithilfe eines benutzerdefinierten Regelsatzes) ein Problem im Code erkannt hat und über eine Empfehlung zur Behebung des Problems verfügt. Wenn Sie eine Glühbirne sehen, klicken Sie darauf, um ausführbare Vorschläge anzuzeigen.

 ![Light Bulbs in Visual Studio Code Editor](./ide/media/vs2015-lightbulbs.png "VS2015_LightBulbs")

## <a name="enjoy-these-additional-ide-improvements"></a>Zusätzliche Verbesserungen der IDE

### <a name="synchronized-settings-roaming-settings"></a>Synchronisierte Einstellungen (Roamingeinstellungen)
 Visual Studio 2013 introduced Synchronized Settings for some of the most commonly configured settings such as Text Editor, Keybindings, Theme & Fonts & Colors, Startup, and Environment Aliases.  In Visual Studio 2015 wird diese Erfahrung verbessert, indem mehr Einstellungen synchronisiert werden und Einstellungen in der ganzen Visual Studio-Anwendungsfamilie wie Professional, Enterprise, Express-SKUs und Blend synchronisiert werden. Wenn Sie sich erstmalig bei Visual Studio 2015 mit demselben Konto anmelden, das Sie in Visual Studio 2013 verwendet haben, werden Sie sehen, dass Ihre synchronisierten Einstellungen aus Visual Studio 2013 angewendet wurden. Sie können auf Ihre Einstellungen zugreifen, indem Sie in **Schnellstart** „sync“ eingeben oder indem Sie zu **Extras > Optionen > Umgebung > Synchronisierte Einstellungen** navigieren.

### <a name="automatic-extension-updates"></a>Automatische Erweiterungsaktualisierungen
 Ihre installierten Visual Studio-Erweiterungen werden nun automatisch aktualisiert, wenn in Visual Studio Gallery eine neue Version verfügbar ist. Unter [Suchen und Verwenden von Visual Studio-Erweiterungen](./ide/finding-and-using-visual-studio-extensions.md) finden Sie Einzelheiten in Bezug auf die Anpassung automatischer Erweiterungsaktualisierungen.

### <a name="title-case-menus"></a>Menüs mit großen Anfangsbuchstaben
 Ihr Wunsch war uns Befehl. Visual Studio-Menüs haben standardmäßig wieder große Anfangsbuchstaben. Wenn Sie doch den GROSSBUCHSTABEN-Stil bevorzugen, können Sie ihn beim Start oder auf der Eigenschaftenseite **Extras > Optionen > Allgemein** festlegen:

 ![Visual Studio 2015 Title Case Main Menu Commands](./ide/media/vs2015-mainmenu.png "VS2015_MainMenu")

### <a name="high-resolution-images-and-touch-support"></a>Hochauflösende Bilder und Touch-Unterstützung
 Die Visual Studio IDE verfügt jetzt über echt hochauflösende Bilder in dichteren Anzeigen (in Bereichen wie Menüs, Kontextmenüs, Toolfenster-Befehlsleisten und einigen Projekten im Projektmappen-Explorer). Und auf einem Touchscreen im Visual Studio-Code-Editor-Fenster können Sie jetzt mit Gesten wie Berühren und Halten, Zusammendrücken, Tippen usw. vergrößern/verkleinern, scrollen, Text markieren und Kontextmenüs aufrufen.

 ![Touch support in editor](./ide/media/vs2015-touchsupport.png "VS2015_TouchSupport")

### <a name="custom-layouts"></a>Benutzerdefinierte Layouts
 Sie können benutzerdefinierte Fensterlayouts erstellen, speichern und ein Roaming dafür ausführen. Sie können beispielsweise ein bevorzugtes Layout zur Verwendung auf dem Desktopcomputer definieren und ein anderes zur Verwendung auf einem Laptop oder einem Gerät mit kleinem Bildschirm. Oder vielleicht bevorzugen Sie ein Layout für ein UI-Projekt und ein anderes für ein Datenbankprojekt. Mit Tastaturzuordnungen können Sie schnell zwischen Layouts wechseln. Diese Layouts sind in jeder Instanz von Visual Studio verfügbar, wenn Sie angemeldet sind. Weitere Informationen finden Sie unter [Erstellen von benutzerdefinierten Fensterlayouts](./misc/create-custom-window-layouts.md).

 ![Visual Studio Custom Layout menu item](./ide/media/vs2015-customlayout.png "VS2015_CustomLayout")

### <a name="notification-hub"></a>Notification Hub
 Die Benutzeroberfläche für den Notification Hub wurde optimiert und kann jetzt schneller durchsucht werden. Es wurden weitere Arten von Benachrichtigungen hinzugefügt, z. B. für Leistungsprobleme, Renderingprobleme und Abstürze, und Sie können Visual Studio jetzt anweisen, eine Benachrichtigung nicht mehr anzuzeigen. Weitere Informationen finden Sie unter [Visual Studio-Benachrichtigungen](./ide/visual-studio-notifications.md).

### <a name="codelens-find-what-happened-to-your-code-enterprise-and-professional-editions-only"></a>CodeLens: Ermitteln, was mit Ihrem Code geschehen ist (nur Enterprise und Professional Editionen)
 Bleiben Sie auf Ihre Arbeit konzentriert, während Sie Informationen zum Code suchen, ohne den Editor zu verlassen. Sie können Änderungen und andere Verläufe für Arbeitselemente, Fehler, Codeüberprüfungen usw. für den Code prüfen, der in Visual Studio Team Services (VSTS) oder in Team Foundation Server (TFS) gespeichert ist.

 Visual Studio Professional und Visual Studio Enterprise ermöglichen jetzt Folgendes:

- Rufen Sie den Verlauf für eine gesamte Codedatei im Visual Studio-Editor ab.

   ![CodeLens: Get code file details](./ide/media/codelensfilelevel.png "CodeLensFileLevel")

- Zeigen Sie ein Diagramm mit den Personen an, die Ihren Code geändert haben. Dadurch können Sie Muster bei den Änderungen Ihres Teams erkennen und ihre Auswirkung bewerten.

   ![CodeLens: See code changes history as a graph](./ide/media/codelens.png "CodeLens")

- Erkennen Sie ganz leicht, wann der Code zuletzt geändert wurde.

- Suchen Sie nach Änderungen in anderen Verzweigungen, die sich auf den Code auswirken.

  Siehe [CodeLens](./ide/find-code-changes-and-other-history-with-codelens.md).

### <a name="design-and-modeling-tools-enterprise-edition-only"></a>Entwurfs- und Modellierungstools (nur Enterprise Edition)
 **Code Maps und Abhängigkeitsdiagramme**

 Zum Verstehen bestimmter Abhängigkeiten im Code in Visual Studio Enterprise können Sie diese visuell darstellen, indem Sie Codezuordnungen erstellen. Sie können dann diese Beziehungen mithilfe der Zuordnung navigieren, die neben dem Code angezeigt wird. Anhand der Codezuordnungen können Sie außerdem die Position im Code beim Arbeiten oder Debuggen von Code nachverfolgen, sodass Sie beim Analysieren des Codeaufbaus weniger lesen müssen.

 In dieser Version haben wir die Kontextmenüs, Codeelemente und Links benutzerfreundlicher gestalten, indem wir die Befehle hinsichtlich Auswählen, Bearbeiten, Verwalten von Gruppen und Ändern des Layouts des Gruppeninhalts in Abschnitte eingesteilt haben. Beachten Sie außerdem, dass Testprojekte in einem anderen Format als andere Projekte angezeigt werden und die Symbole für Elemente in der Zuordnung passender gestaltet wurden.

 ![Show selected items on a new code map](./ide/media/codemapsshowonnewmap.png "CodeMapsShowOnNewMap")

 Zu den weiteren Verbesserungen gehören:

- **Verbesserte Top-Down-Diagramme**. Für mittlere bis große Visual Studio-Projektmappen können Sie nun ein vereinfachtes Architektur-Menü verwenden, um weitere nützliche Codezuordnungen für Ihre Lösung abzurufen. Die Assemblys der Projektmappe werden nach den Projektmappenordnern gruppiert, dadurch können Sie Sie im Kontext betrachten und die Mühen nutzen, die Sie in die Strukturierung der Lösung gesteckt haben. Ihnen werden sofort Projekt- und Assemblyverweise und anschließend die Linktypen angezeigt. Darüber hinaus werden die Assemblys, die sich außerhalb der Projektmappe befinden, in einer kompakteren Weise gruppiert.

- **Testprojekte sind unterschiedlich formatiert und können gefiltert werden**. Sie können jetzt einfach und schnell Testprojekte in der Übersicht ermitteln, da sie unterschiedlich formatiert sind. Sie können auch herausgefiltert werden, damit Sie sich auf den Arbeitscode der Anwendung konzentrieren können.

- **Vereinfachte externe Abhängigkeitslinks**. Abhängigkeitslinks stellen nicht mehr die Vererbung von System.Object, System.ValueType, System.Enum und System.Delegate dar, dadurch lassen sich externe Abhängigkeiten in der Codezuordnung leichter auffinden.

- **Drilldown-Abhängigkeitslinks berücksichtigen Filter**. Dadurch erhalten Sie ein nützliches, klar strukturiertes Diagramm beim Erweitern, damit Sie die Rolle für einen Abhängigkeitslink besser nachvollziehen können. Das Diagramm ist weniger überladen und berücksichtigt die Linkfilteroptionen, die Sie ausgewählt haben.

- **Codeelemente werden zu einer Codezuordnung mit Kontext hinzugefügt**. Da Diagramme jetzt mit ihrem Kontext (bis zum Assembly- und Projektmappenordner, den Sie ggf. herausfiltern können), erhalten Sie weitere nützliche Diagramme beim Ziehen und Ablegen von Codeelementen aus dem Projektmappen-Explorer, der Klassenansicht und dem Objektkatalog; oder beim Auswählen von Elementen im Projektmappen-Explorer und beim Auswählen der Option „In Codezuordnung anzeigen“.

- **Reaktive Codezuordnungen schneller abrufen**. Drag & Drop-Vorgänge erzeugen ein sofortiges Ergebnis, und die Links zwischen Knoten werden wesentlich schneller erstellt, ohne Auswirkungen auf nachfolgende von Benutzern initiierte Vorgänge wie z. B. das Erweitern eines Knotens oder das Anfordern mehr Knoten zu haben. Beim Erstellen von Codezuordnungen ohne die Lösung zu entwickeln, werden nun alle Ausnahmefälle, wie z. B. wenn Assemblys nicht erstellt werden, verarbeitet.

- **Überspringen Sie das Neuerstellen der Projektmappe.** Bietet eine bessere Leistung beim Erstellen und Bearbeiten von Diagrammen.

- **odeelementknoten und Gruppen filtern**. Sie können Ihre Zuordnungen schnell basierend auf der Kategorie durch Ein- oder Ausblenden von Codeelementen und durch das Gruppieren von Codeelementen nach Projektmappenordner, Assemblys, Namespaces, Projektordner und Typen organisieren.

- **Filtern Sie Beziehungen, damit Diagramme leichter zu lesen sind**. Das Filtern von Links gilt jetzt auch für gruppenübergreifende Links, dadurch gestaltet sich die Arbeit mit dem Filterfenster weniger aufwendig als in vorherigen Versionen.

- **Erstellen Sie Diagrammen aus der Klassenansicht und im Objektbrowser**. Das Ziehen und Ablegen von Dateien und Assemblys in einer neuen oder vorhandenen Zuordnung funktioniert aus den Klassenansicht- und Objektbrowser-Fenstern.

  Siehe [Map dependencies across your solutions](./modeling/map-dependencies-across-your-solutions.md).

  **Andere Entwurfs- und Modellierungsänderungen in diesem Release:**

- **Ebenendiagramme**. Aktualisieren Sie diese Diagramme mit der Klassenansicht und dem Objektbrowser. Mithilfe von Ebenendiagrammen können Sie die gewünschten Abhängigkeiten für Ihre Software beschreiben, um die Software-Entwicklungsanforderungen zu erfüllen. Halten Sie den Code anhand dieses Aufbaus konsistent, indem Sie Code finden, der diese Einschränkungen nicht erfüllt und zukünftigen Code anhand dieser Baseline zu validieren.

- **UML-Diagramme**. Es ist nicht mehr möglich, UML-Klassendiagramme und Sequenzdiagramme im Code zu erstellen. Sie können dieses Diagramm jedoch weiterhin mithilfe der neuen UML-Elemente erstellen.

- **Architektur-Explorer**. Sie können den Architektur-Explorer nicht mehr zum Erstellen von Diagrammen verwenden. Aber Sie können weiterhin den Projektmappen-Explorer verwenden.

## <a name="visual-studio-extensibility-tools"></a>Visual Studio-Erweiterbarkeitstools
 Es war noch nie einfacher, Visual Studio-Erweiterbarkeitstools (VS SDK und Vorlagen) zu installieren, da sie nun während des Setups als optionale Komponente enthalten sind.  Mit den Erweiterbarkeitstools können Entwickler Erweiterungen schreiben, um Visual Studio anzupassen und ihm Features hinzuzufügen. Weitere Informationen über die Visual Studio-Erweiterbarkeit finden Sie unter [Visual Studio SDK](./extensibility/visual-studio-sdk.md).

 Wenn Sie die Erweiterbarkeitstools in Ihre benutzerdefinierte Installation einbeziehen möchten, können Sie sie unter **Features / Allgemeine Tools / Visual Studio-Erweiterbarkeitstools**finden.  Sie können die Erweiterbarkeitstools auch später installieren, indem Sie das Dialogfeld **Neues Projekt** öffnen und das Element **Visual Studio-Erweiterbarkeitstools installieren** unter **Visual C# / Erweiterbarkeit**auswählen.

## <a name="please-give-feedback"></a>Senden Sie uns Ihr Feedback
 Warum sollten Sie dem Visual Studio-Team ein Feedback senden? Weil wir das Feedback unserer Kunden ernst nehmen. Wir prüfen jedes Feedback, das in unser Feedbacksystem gelangt. Ihr Feedback gibt Anstoß für viele unserer Initiativen.

### <a name="send-a-smile"></a>Ein Lächeln senden
 Wenn Sie uns mitteilen, was Ihnen gefällt, können wir besser verstehen, ob wir Ihre Erwartungen erfüllen oder übertreffen. Wenn wir neue Features entwickeln und implementieren, nutzen wir für unsere Designentscheidungen Daten über die Features, die Ihnen gefallen. Teilen Sie uns deshalb mit, wenn Ihnen ein Feature in Visual Studio gefällt. Es ist einfach und direkt in der IDE möglich.

 Klicken Sie einfach auf das gelbe Smileysymbol in der Titelleiste, sagen Sie uns, was Ihnen gefallen hat, und klicken Sie auf die Schaltfläche **Lächeln senden** .

 Das ist alles! Wir leiten Ihr Feedback an das richtige Team weiter. Dort wird man sich auf die Schulter klopfen, aber auch gleich nach weiteren Möglichkeiten suchen, Sie noch mehr zu erfreuen.

### <a name="send-a-frown"></a>Ein Stirnrunzeln senden
 Zu hören, an welchen Punkten wir das Produkt verbessern müssen, hilft uns, unseren Nachholbedarf zu verwalten, indem wir zuerst die Dinge in den Fokus rücken, die unseren Kunden am wichtigsten sind. Wenn Sie sich über etwas ärgern, teilen Sie uns dies mithilfe des Features **Stirnrunzeln senden** direkt über die IDE mit. Auch dieser Prozess ist ganz einfach:

 Klicken Sie auf das gelbe Smileysymbol in der Titelleiste, und klicken Sie dann auf **Stirnrunzeln senden**. Sagen Sie uns, was Ihnen nicht gefallen hat, und klicken Sie dann auf die Schaltfläche "Stirnrunzeln senden". Weitere Informationen finden Sie unter [Talk to Us](./ide/talk-to-us.md).

### <a name="report-crashes-hangs-and-performance-issues"></a>Berichte über Abstürze, Hängen und Leistungsprobleme
 Gelegentlich reicht eine kurze Mitteilung bei einem Stirnrunzeln nicht aus, um die vollständige Auswirkung von Vorkommnissen darzustellen, die Ihnen nicht gefallen. Bei jedem Hängen, Absturz oder Leistungsproblem können Sie mit dem Dialogfeld, das nach dem Senden eines Stirnrunzelns angezeigt wird, die Schritte zur Reproduktion des Problems, Crashdumps und Ablaufverfolgungsdateien ohne weiteres weitergeben.

 Senden Sie zuerst ein Stirnrunzeln wie oben beschrieben. Im angezeigten Dialogfeld können Sie Ihrem Feedback eines der Standardtags zuweisen oder Ihr eigenes Tag erstellen. Tags helfen uns, Ihr Feedback an das richtige Featureteam zu leiten. Wählen Sie in der Dropdownliste **Kategorie auswählen** die für das gemeldete Problem passende Option aus, und führen Sie anschließend die Schritte zum Reproduzieren des Problems aus. Detaillierte Schritte zur Verwendung von Visual Studio für Feedbackmeldungen stehen ebenfalls zur Verfügung. For more information, see [Visual Studio Send a Smile Instructions](https://msdn.microsoft.com/library/5cc9b67a-54d0-41b0-aa8f-80dff4475a6b).

## <a name="see-also"></a>Siehe auch

* [Erstellen von plattformübergreifenden Apps mit Apache Cordova](https://msdn.microsoft.com/library/34d3c1be-22b3-4812-97fb-10b4e8ad2134)
* [Erstellen von Apps mit nativer Benutzeroberfläche über Xamarin in Visual Studio](./cross-platform/build-apps-with-native-ui-using-xamarin-in-visual-studio.md)
* [Erstellen von plattformübergreifenden Apps mit Visual C++](./misc/build-cross-platform-mobile-apps-with-visual-cpp.md)
* [Generieren von Komponententests für Code mit IntelliTest](./test/generate-unit-tests-for-your-code-with-intellitest.md)
* [Arbeiten mit mehreren Benutzerkonten](./ide/work-with-multiple-user-accounts.md)
* [Erstellen von benutzerdefinierten Fensterlayouts](./misc/create-custom-window-layouts.md)
* [Ausführen von schnellen Aktionen mit Glühbirnen](./ide/perform-quick-actions-with-light-bulbs.md)
* [Neues in Visual Studio 2017](/visualstudio/ide/how-to-report-a-problem-with-visual-studio-2017)