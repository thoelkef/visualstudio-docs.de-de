---
title: "Erstellen von plattform&#252;bergreifenden Apps mit Visual C++ | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 44c16342-6951-4852-95b0-b97ae858ee50
caps.latest.revision: 13
caps.handback.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "douge"
---
# Erstellen von plattform&#252;bergreifenden Apps mit Visual C++
Sie können mit Visual C\+\+ für die plattformübergreifende Mobilgeräteentwicklung plattformübergreifenden Code für Android\-, iOS\- und Windows\-Geräte schreiben.  Dies ist eine optionale Funktion in Visual Studio 2015, die eine plattformübergreifende Entwicklung für iOS, Android und Windows mithilfe von Visual C\+\+ ermöglicht.  
  
 Sie können Visual Studio zum Generieren von freigegebenen Bibliotheken mit Standard\-C\+\+\-Code für klassische Windows\-Desktopanwendungen, universelle Windows\-Apps sowie iOS\- und Android\-Plattformen verwenden.  Sie können systemeigene Apps für Windows\- und Android\-Plattformen generieren, indem Sie einfach Visual C\+\+ und die in Visual Studio integrierten Drittanbietertools nutzen.  Auf einem Mac können Sie Visual Studio verwenden, um C\+\+\-Code für iOS\-Apps zu erstellen und zu debuggen, die auf Ihrem Mac generiert und bereitgestellt werden.  
  
> [!NOTE]
>  Standardmäßig unterstützt Visual C\+\+ für die plattformübergreifende Mobilgeräteentwicklung Android\-API\-Ebene 19 und 21 und zielt auf Android 4.4 und 5.0 ab.  Weitere API\-Ebenen können mit dem SDK Manager installiert werden.  Der Visual Studio C\+\+ Android\-Debugger erfordert, dass auf den Zielemulatoren oder \-geräten mindestens Android\-API\-Ebene 17 \(Version 4.2\) oder höher ausgeführt wird.  
  
 Dieser Artikel beschreibt die ersten Schritte in Bezug auf das Erstellen von plattformübergreifenden Apps mit Visual C\+\+ für die plattformübergreifende Mobilgeräteentwicklung in Visual Studio 2015:  
  
 [Anforderungen](#req)   
 [Beschaffung der Tools](#GetTools)  
 [Erstellen eines neuen Android Native Activity-Projekts](#Create)  
 [Generieren und Ausführen der Android-Native Activity-App](#BuildHello)  
  
##  <a name="req"></a> Anforderungen  
  
-   Informationen über die Installationsanforderungen finden Sie unter [Visual Studio 2015\-Systemanforderungen](https://www.visualstudio.com/visual-studio-2015-system-requirements-vs).  
  
    > [!IMPORTANT]
    >  Wenn Sie Windows 7 oder Windows Server 2008 R2 verwenden, können Sie Code für klassische Windows\-Anwendungen, Android Native Activity\-Apps und \-Codebibliotheken sowie Apps und Codebibliotheken für iOS, jedoch keine Windows Store\- oder universellen Windows\-Apps entwickeln.  
  
 Zum Erstellen von Anwendungen für bestimmte Plattformen bestehen einige zusätzliche Anforderungen:  
  
-   Der Visual Studio\-Emulator für Android und die Windows Phone\-Emulatoren erfordern einen Computer, auf dem Hyper\-V ausgeführt werden kann.  Weitere Informationen finden Sie unter den [Systemanforderungen](http://msdn.microsoft.com/de-de/4d5bb438-231a-4cd2-84b7-e9660b0e3baf) des Emulators.  
  
-   Die im Lieferumfang des Android\-SDK enthaltenen  x86\-Android\-Emulatoren funktionieren am besten auf Computern, auf denen der Intel HAXM\-Treiber ausgeführt werden kann.  Dieser Treiber erfordert einen Intel x64\-Prozessor mit VT\-x und Execute Disable Bit\-Unterstützung.  Weitere Informationen finden Sie unter [Installationsanweisungen für Intel® Hardware Accelerated Execution Manager – Microsoft Windows](http://go.microsoft.com/fwlink/p/?LinkId=536385).  
  
-   Für die Entwicklung von Apps für iOS werden ein iOS\-Entwicklerprogrammkonto und ein Mac benötigt, auf dem Xcode 6 ausgeführt werden kann.  
  
##  <a name="GetTools"></a> Beschaffung der Tools  
 Visual C\+\+ für die plattformübergreifende Mobilgeräteentwicklung ist eine optionale Komponente, die in Visual Studio 2015 enthalten ist.  Wechseln Sie zur Seite [Visual Studio 2015 – Downloads](http://go.microsoft.com/fwlink/?linkid=517106), und laden Sie Visual Studio 2015 herunter.  
  
 Der Installer für Visual Studio 2015 umfasst eine Option zur Unterstützung der plattformübergreifenden Entwicklung für mobile Geräte.  Diese bietet die Option zum Installieren von Visual C\+\+ Mobile Development sowie der folgenden gängigen Tools und SDKs.  Bei den meisten handelt es sich um Open Source\-Software, die für die plattformübergreifende Unterstützung erforderlich ist.  
  
-   Android Native Development Kit \(R10E, 32 Bit\) ist für den Android\-Buildprozess erforderlich.  
  
-   Android SDK, Apache Ant und Java SE Development Kit sind für den Android\-Buildprozess erforderlich.  
  
-   Microsoft Visual Studio Emulator für Android ist ein schneller, leistungsfähiger Emulator für die Android\-Entwicklung.  
  
 Ausführliche Installationsanweisungen finden Sie unter [Installieren von Visual C\+\+ für die plattformübergreifende mobile Entwicklung](../cross-platform/install-visual-cpp-for-cross-platform-mobile-development.md).  
  
 Zum Erstellen von Code für iOS müssen Sie einen Remote\-Build\-Agent auf Ihrem Mac einrichten und in Visual Studio verbinden.  Detaillierte Installations\- und Konfigurationsanweisungen finden Sie unter [Installieren und Konfigurieren von Tools zum Erstellen mit iOS](../cross-platform/install-and-configure-tools-to-build-using-ios.md).  
  
##  <a name="Create"></a> Erstellen eines neuen Android Native Activity\-Projekts  
 Sie können Visual C\+\+ für plattformübergreifende mobile Entwicklung verwenden, um eine vollständige Android\-App mithilfe von C\+\+ zu erstellen, zu generieren, auszuführen und zu debuggen.  Visual Studio enthält eine Vorlage für ein Android\-Native Activity\-Projekt, das Ihnen beim Einstieg helfen kann.  
  
 In diesem Lernprogramm erstellen Sie zunächst ein neues Projekt, bevor Sie die standardmäßige App generieren und ausführen.  
  
 Stellen Sie vor dem Erstellen eines neuen Projekts sicher, dass Sie alle Systemvoraussetzungen erfüllen und Visual C\+\+ für die plattformübergreifende Mobilgeräteentwicklung für Visual Studio installiert haben.  Weitere Informationen finden unter [Installieren von Visual C\+\+ für die plattformübergreifende mobile Entwicklung](../cross-platform/install-visual-cpp-for-cross-platform-mobile-development.md)  
  
#### So erstellen Sie ein neues Projekt  
  
1.  Öffnen Sie Visual Studio.  Wählen Sie in der Menüleiste **Datei**, **Neu**, **Projekt** aus.  
  
2.  Wählen Sie im Dialogfeld **Neues Projekt** unter **Vorlagen** die Option **Visual C\+\+**, **Plattformübergreifend** und dann die Vorlage **Native\-Activity Application \(Android\)** aus.  
  
3.  Vergeben Sie an die App einen Namen wie etwa `MyAndroidApp` \(ohne Leerzeichen\), und wählen Sie dann **OK** aus.  
  
     ![Erstellen eines Native Activity&#45;Projekts](../cross-platform/media/cppmdd_newproject.PNG "CppMDD\_NewProject")  
  
     Visual Studio erstellt die neue Projektmappe und öffnet den Projektmappen\-Explorer.  
  
 Die neue Android Native Activity\-App\-Projektmappe enthält zwei Projekte:  
  
-   **MyAndroidApp.NativeActivity** enthält die Verweise und den Verbindungscode, damit Ihre App als eine systemeigene Aktivität auf Android ausgeführt werden kann.  Die Implementierung der Einstiegspunkte aus dem Verbindungscode befindet sich in "main.cpp".  Vorkompilierte Header befinden sich in "pch.h".  Ihr App\-Projekt wird in eine freigegebene Bibliotheksdatei \(SO\) kompiliert, die durch das Packaging\-Projekt ausgewählt wird.  
  
-   **MyAndroidApp.Packaging** erstellt die APK\-Paketdatei für die Bereitstellung auf einem Android\-Gerät oder \-Emulator.  Dieses enthält die Ressourcen und die Datei "AndroidManifest.xml", wo Sie Manifesteigenschaften festlegen.  Es enthält zudem die Datei "build.xml", die den Ant\-Buildprozess steuert.  Es ist standardmäßig als Startprojekt festgelegt, sodass es bereitgestellt und direkt in Visual Studio ausgeführt werden kann.  
  
##  <a name="BuildHello"></a> Generieren und Ausführen der Android\-Native Activity\-App  
 Erstellen und führen Sie die App aus, die durch die Vorlage generiert wurde, um Ihre Installation und Einrichtung zu überprüfen.  Die Vorlage legt die Projektmappenkonfiguration standardmäßig auf „Debug“ und die Projektmappenplattform auf „x86“ fest, um die App im Microsoft Visual Studio\-Emulator für Android auszuführen.  Wenn Sie Ihre App auf einem anderen Ziel testen möchten, laden Sie den Zielemulator, oder verbinden Sie das Gerät mit Ihrem Computer.  
  
#### So erstellen Sie die standardmäßige Native Activity\-App und führen diese aus  
  
1.  Wählen Sie in der Menüleiste **Erstellen**, **Projektmappe erstellen**.  
  
     Das Fenster **Ausgabe** zeigt die Ausgabe des Buildprozesses für die zwei Projekte in der Projektmappe an.  
  
2.  Wählen Sie eins der Visual Studio\-Emulatorprofile als Ihr Bereitstellungsziel aus.  
  
     Wenn Sie andere Emulatoren installiert oder mit einem Android\-Gerät verbunden haben, können Sie sie aus der Bereitstellungsziel\-Dropdownliste auswählen.  
  
3.  Drücken Sie F5, um mit dem Debuggen zu beginnen, oder UMSCHALT\+F5, um ohne Debuggen zu beginnen.  
  
     So in etwa sieht die standardmäßige App im Visual Studio\-Emulator für Android aus.  
  
     ![Der Emulator führt Ihre App aus](~/docs/cross-platform/media/cppmdd_emulator_running_app.PNG "CppMDD\_Emulator\_Running\_App")  
  
    > [!TIP]
    >  Visual Studio startet den Emulator, wobei das Laden und Bereitstellen Ihres Codes einige Sekunden in Anspruch nimmt.  Nachdem Ihre App gestartet wurde, können Sie Haltepunkte festlegen und den Debugger verwenden, um den Code schrittweise zu durchlaufen, lokale Variablen zu prüfen und Werte anzuzeigen.  
  
4.  Drücken Sie UMSCHALTTASTE\+F5, um das Debuggen zu beenden.  
  
     Der Emulator ist ein separater Prozess, der weiterhin ausgeführt wird.  Sie können Ihren Code mehrfach auf demselben Emulator bearbeiten, kompilieren und bereitstellen.  
  
## Siehe auch  
 [Herunterladen von Visual Studio 2015](http://go.microsoft.com/fwlink/?linkid=517106)