---
title: "The application cannot start. | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.message.0x800A0001"
  - "vs.message.VB_E_IDACANTBOOT"
ms.assetid: ffc123a0-99e1-4e9d-8f6e-34aa357bf98f
caps.latest.revision: 13
caps.handback.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# The application cannot start.
Aufgrund eines unerwarteten Fehlers konnte Visual Studio nicht gestartet werden.  Dieser Fehler tritt auf, wenn eine der folgenden Situationen vorliegt:  
  
-   Die integrierte Entwicklungsumgebung \(IDE\) konnte Msxml3.dll nicht laden.  
  
-   Die IDE konnte Mso.dll nicht laden.  
  
-   Die IDE konnte DTE.olb nicht laden.  
  
-   Der Lizenzschlüssel für Visual Studio wurde während des Setups nicht erstellt.  
  
-   Die Skriptblockierung ist aktiviert, wodurch kein Skriptcode ausgeführt werden kann.  
  
-   Das Setup für .NET Framework, eine von Visual Studio benötigte Komponente, konnte kein gültiges systemeigenes Image für mscorlib.dll generieren.  
  
-   Der Klez\-Virus ist auf Ihrem Computer vorhanden.  
  
 Verwenden Sie die folgenden Verfahren, um diesen Fehler zu beheben.  
  
> [!WARNING]
>  Einige dieser Lösungen erfordern eine Änderung des Registrierungsschlüssels.  Wenn Sie den Registrierungs\-Editor nicht ordnungsgemäß verwenden, können schwerwiegende Probleme auftreten, die eine Neuinstallation des Betriebssystems erforderlich machen.  Microsoft kann nicht garantieren, dass Probleme, die aus der nicht ordnungsgemäßen Verwendung des Registrierungs\-Editors entstehen, behoben werden können.  Sie verwenden den Registrierungs\-Editor auf eigene Gefahr.  
  
 Die IDE konnte Msxml3.dll nicht laden.  
 Die Beta\-Version von MSXML 4.0 Technology Preview von Juli 2001 hatte einen Computerzustand zur Folge, der dieses Verhalten verursacht.  Gehen Sie folgendermaßen vor, um die Msxml3.dll\-Registrierung zu reparieren:  
  
### Deinstallieren von Msxml4.dll  
  
1.  Klicken Sie im Menü **Start** auf **Ausführen**.  
  
2.  Geben Sie `regsvr32 /u c:\winnt\system32\msxml4.dll` in das Textfeld **Öffnen** ein, und klicken Sie auf **OK**.  
  
### Herunterladen und Installieren des Sicherheitsupdates für MSXML  
  
1.  Laden Sie das neueste Sicherheitsupdate für die Version von MSXML herunter, die auf Ihrem Computer installiert ist: [http:\/\/www.microsoft.com\/windows\/ie\/downloads\/critical\/q317244\/download.asp](http://www.microsoft.com/windows/ie/downloads/critical/q317244/download.asp).  
  
2.  Führen Sie die EXE\-Datei für das Sicherheitsupdate aus.  
  
### Herunterladen und Übernehmen der aktualisierten Registrierungswerte  
  
1.  Laden Sie die aktualisierten Registrierungswerte von [http:\/\/download.microsoft.com\/download\/VisualStudioNET\/fix\/1.0\/WIN98MeXP\/Fixxml4.exe](http://download.microsoft.com/download/VisualStudioNET/fix/1.0/WIN98MeXP/Fixxml4.exe) herunter.  
  
2.  Doppelklicken Sie auf fixxml4.exe, und entpacken Sie die Dateien.  
  
3.  Suchen Sie nach Fixxml4.reg, und doppelklicken Sie auf die Datei, um die Registrierungswerte zu aktualisieren.  
  
 Die IDE konnte Mso.dll nicht laden.  
 Verwenden Sie die folgende Liste, um Probleme mit Mso.dll zu beheben.  
  
### Microsoft Office  
  
-   Deinstallieren Sie alle Microsoft Office XP Beta\-Versionen auf Ihrem Computer.  
  
-   Reparieren Sie Office XP über die Option „Software“.  
  
-   Überprüfen Sie im Registrierungs\-Editor den folgenden Registrierungsschlüssel:  
  
     `[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\7.0\Path] "MSO"="C:\Program Files\Common Files\Microsoft Shared\Office10\MSO.DLL"`  
  
 Die IDE konnte DTE.olb nicht laden.  
 So beheben Sie diesen Fehler:  
  
### Registrieren von Dte.olb  
  
1.  Klicken Sie im Menü **Start** auf **Ausführen**.  
  
2.  Geben Sie `regsvr32 C:\Program Files\Common Files\Microsoft Shared\MSEnv\DTE.OLB` in das Textfeld **Öffnen** ein, und klicken Sie auf **OK**.  
  
 Der Lizenzschlüssel für Visual Studio wurde während des Setups nicht erstellt.  
 Wenn der Begrüßungsbildschirm für Visual Studio keine Liste der installierten Produkte enthält und keine Informationen über die Person aufgeführt werden, die das Produkt installiert hat, fehlt der Lizenzschlüssel.  Auch wenn Visual Studio nicht im Dialogfeld „Software“ aufgeführt ist, fehlt der Lizenzschlüssel.  
  
 So korrigieren Sie dieses Problem:  
  
### Erstellen eines Lizenzschlüssels für Visual Studio  
  
-   Entfernen Sie Visual Studio vollständig vom Computer, und installieren Sie das Produkt dann neu.  
  
 Die Skriptblockierung ist aktiviert, wodurch kein Skriptcode ausgeführt werden kann.  
 Wenn eine Anwendung von einem Drittanbieter die Skriptblockierung aktiviert hat, wird die IDE angezeigt und dann wieder ausgeblendet.  
  
-   Stellen Sie zur Behebung dieses Problems sicher, dass die Funktion zum Blockieren von Skript ordnungsgemäß funktioniert.  
  
 Das Setup für .NET Framework, eine von Visual Studio benötigte Komponente, konnte kein gültiges systemeigenes Image für mscorlib.dll generieren.  
 Wenn der Begrüßungsbildschirm für Visual Studio kurz angezeigt und dann ausgeblendet wird, ist möglicherweise kein gültiges systemeigenes Image der Datei Mscorlib.dll vorhanden.  Diese Datei wird beim Setup von .NET Framework im Verzeichnis \\%windir%\\assembly\\NativeImages1\_v1.0.3705\\mscorlib erstellt.  
  
 So beheben Sie dieses Problem:  
  
### Erstellen einer gültigen Mscorlib.dll\-Datei  
  
1.  Deinstallieren Sie .NET Framework, und installieren Sie das Programm dann neu.  
  
 Der Klez\-Virus ist auf Ihrem Computer vorhanden.  
 Wenn Ihr Computer mit dem Klez\-Virus infiziert ist, wird der Fehler „Die Anwendung kann nicht gestartet werden“ angezeigt.  Es wird empfohlen, dass Sie Ihre Antivirus\-Software aktualisieren und dann den Computer auf Viren überprüfen.