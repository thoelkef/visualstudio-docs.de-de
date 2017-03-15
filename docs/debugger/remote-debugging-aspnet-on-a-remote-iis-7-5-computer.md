---
title: "Remotedebuggen von ASP.NET auf einem Remotecomputer mit IIS 7.5 | Microsoft Docs"
ms.custom: ""
ms.date: "12/02/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "hero-article"
ms.assetid: 573a3fc5-6901-41f1-bc87-557aa45d8858
caps.latest.revision: 8
caps.handback.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Remotedebuggen von ASP.NET auf einem Remotecomputer mit IIS 7.5
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Sie können eine ASP.NET\-Webanwendung auf einem Windows Server 2008 R2\-Computer mit IIS 7.5 bereitstellen und für das Remotedebuggen einrichten. Nachfolgend wird das Einrichten und Konfigurieren einer Visual Studio 2015 MVC 4.5.2\-Anwendung erläutert.  
  
## Erstellen der Anwendung auf dem Visual Studio\-Computer  
  
1.  Erstellen Sie eine neue MVC ASP.NET\-Anwendung. \(Wählen Sie **Datei \/ Neu \/ Projekt** und dann **Visual C\# \/ Web \/ ASP.NET\-Webanwendung** aus. Im **ASP.NET 4.5.2**\-Vorlagenabschnitt wählen Sie **MVC** aus. Brechen Sie die Seite **Microsoft Azure Webanwendung konfigurieren** ab. \) Nennen Sie sie **MeinMVC**.  
  
2.  Öffnen Sie die Datei „HomeController.cs“, und legen Sie einen Haltepunkt in der `About()`\-Methode fest.  
  
3.  Klicken Sie im **Projektmappen\-Explorer** mit der rechten Maustaste auf den Projektknoten, und wählen Sie **Veröffentlichen** aus.  
  
4.  Wählen Sie für **Veröffentlichungsziel auswählen** die Option **Benutzerdefiniert** aus, und nennen Sie das Profil **MeinMVC**. Klicken Sie auf **Weiter**.  
  
5.  Legen Sie auf der Registerkarte **Verbindung** das Feld **Veröffentlichungsmethode** auf **Dateisystem** und das Feld **Zielspeicherort** auf ein lokales Verzeichnis fest. Klicken Sie auf **Weiter**.  
  
6.  Legen Sie die Konfiguration auf **Debuggen** fest. Klicken Sie auf **Veröffentlichen**.  
  
     Die Anwendung sollte in das lokale Verzeichnis veröffentlicht werden.  
  
## Bereitstellen der Anwendung auf dem Windows Server\-Remotecomputer  
 In diesem Abschnitt wird davon ausgegangen, dass auf dem Windows Server 2008 R2\-Computer IIS bereits aktiviert ist.  
  
1.  Sie installieren Sie ASP.NET  
  
     **C:\\Windows\\Microsoft.NET\\Framework\(64\)\\v4.0.30319\\aspnet\_regiis.exe \-ir**  
  
2.  Kopieren Sie das ASP.NET\-Projektverzeichnis vom Visual Studio\-Computer in ein lokales Verzeichnis \(das wir **C:\\Publish** nennen\) auf dem Windows Server\-Computer.  
  
3.  Stellen Sie sicher, dass in der Datei „web.config“ die richtige Version von .NET Framework aufgeführt ist.  Die standardmäßig auf diesem Computer installierte .NET Framework\-Version ist 4.0.30319, aber wir haben eine ASP.NET 4.5.2\-Version erstellt. Wenn diese Version auf dem Windows Server\-Computer nicht installiert ist, müssen Sie die Version ändern:  
  
    ```xml  
    <system.web> <authentication mode="None" /> <compilation debug="true" targetFramework="4.0.30319" /> <httpRuntime targetFramework="4.0.30319" /> </system.web>  
  
    ```  
  
4.  Öffnen Sie den **Internetinformationsdienste\-Manager \(IIS\)**, und navigieren Sie zu **Websites**.  
  
5.  Klicken Sie mit der rechten Maustaste auf den Knoten **Standardwebsite**, und wählen Sie **Anwendung hinzufügen** aus.  
  
6.  Legen Sie das Feld **Alias** auf **MeinMVC** und das Feld „Anwendungspool“ auf **ASP.NET v4. 0** fest. Legen Sie den **physischen Pfad** auf **C:\\Publish** fest \(in den Sie das ASP.NET\-Projektverzeichnis kopiert haben\).  
  
7.  Zum Testen der Bereitstellung klicken Sie mit der rechten Maustaste auf **Standardwebsite**, und wählen Sie **Durchsuchen** aus. Es sollte die Webseite angezeigt werden.  
  
## Installieren des Remotedebuggers auf dem Windows Server\-Computer  
 Weitere Informationen zum Herunterladen des Remotedebuggers finden Sie unter [Remotedebugging](../debugger/remote-debugging.md).  
  
 Zum Remotedebuggen von ASP.NET\-Anwendungen können Sie entweder den Remotedebugger als Dienst starten oder die Remotedebuggeranwendung als Administrator ausführen. Ausführliche Informationen zum Ausführen des Remotedebuggers als Dienst finden Sie unter [Remotedebugging](../debugger/remote-debugging.md).  
  
## Anfügen an die ASP.NET\-Anwendung vom Visual Studio\-Computer aus  
  
-   Öffnen Sie auf dem Visual Studio\-Computer die Projektmappe **MeinMVC**.  
  
-   Klicken Sie in Visual Studio auf **Debuggen \/ An den Prozess anhängen**.  
  
-   Legen Sie das Feld „Qualifizierer“ auf **\<Name des Remotecomputers\>:4020** fest.  
  
-   Im Fenster sollten einige Prozesse **Verfügbare Prozesse** angezeigt werden.  
  
-   Aktivieren Sie **Prozesse aller Benutzer anzeigen**.  
  
-   Suchen Sie nach **w3wp.exe**, und klicken Sie auf **Anfügen**.  
  
-   Öffnen Sie die Website des Remotecomputers. Navigieren Sie in einem Browser zu **http:\/\/\<Name des Remotecomputers\>**.  
  
-   Es sollte die ASP.NET\-Webseite angezeigt werden. Klicken Sie auf **Info**.  
  
     Der Haltepunkt sollte in Visual Studio erreicht werden.