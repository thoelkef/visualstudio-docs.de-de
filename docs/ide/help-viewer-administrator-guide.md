---
title: "Help Viewer-Administratorhandbuch | Microsoft Docs"
ms.custom: ""
ms.date: "12/02/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 4340c69f-b96b-4932-bb82-38b16a5ab149
caps.latest.revision: 13
caps.handback.revision: 13
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Help Viewer-Administratorhandbuch
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Der Help Viewer ermöglicht das Verwalten der lokal installierten Hilfe in Netzwerkumgebungen mit oder ohne Internetzugriff.  Der Inhalt der lokalen Hilfe wird pro Computer konfiguriert.  Standardmäßig benötigen Benutzer Administratorrechte, um ihre lokal installierte Hilfe zu aktualisieren.  
  
 Wenn in Ihrer Netzwerkumgebung Clients Zugriff auf das Internet haben, ermöglicht der Help Viewer das Verwenden von Befehlszeilenskripts, um lokale Hilfeinhalte über das Internet bereitzustellen.  
  
 Wenn Clients in Ihrer Netzwerkumgebung nicht auf das Internet zugreifen können, ermöglicht der Help Viewer das Bereitstellen lokaler Hilfeinhalte über das Intranet oder eine Netzwerkfreigabe.  Sie können auch die Hilfeoptionen der Visual Studio\-IDE deaktivieren, beispielsweise Online\- oder Offlinehilfe, die Installation der Inhalte beim ersten Starten der IDE, das Angeben eines intranetbasierten Inhaltsdiensts sowie das Verwalten von Inhalt mit Überschreibungen des Registrierungsschlüssels.  
  
 Die grundlegende Syntax lautet:  
  
 \<*path to*\>\\HlpCtntmgr.exe \/operation \<*argument*\> \/catalogname \<*name*\> \/locale \<*locale*\> \/sourceuri \<*.msha path or URL*\>  
  
 Weitere Informationen zur Befehlszeilensyntax von "HlpCtntMgr.exe" finden Sie unter [Befehlszeilenargumente für den Hilfeinhalts\-Manager](../ide/command-line-arguments-for-the-help-content-manager.md).  
  
 Weitere Informationen zum Generieren von Inhalten, zum Erstellen eines Endpunkts für den Intranetdienst und zu ähnlichen Aktionen finden Sie im SDK des Help Viewer.  
  
## Bereitstellen des lokalen Hilfeinhalts über das Internet  
 Sie können den MSDN Content Package\-Dienst verwenden, um lokale Hilfeinhalte über das Internet auf Clientcomputern bereitzustellen.  Verwenden Sie folgende Syntax:  
  
 \\\<*path to*\>\\v2.2\\HlpCtntmgr.exe \/operation \<*name*\> \/catalogname \<*catalog name*\> \/locale \<*locale*\>  
  
 Weitere Informationen zur Befehlszeilensyntax von "HlpCtntMgr.exe" finden Sie unter [Befehlszeilenargumente für den Hilfeinhalts\-Manager](../ide/command-line-arguments-for-the-help-content-manager.md).  
  
 Anforderungen:  
  
-   Clientcomputer müssen Zugriff auf das Internet haben.  
  
-   Benutzer müssen über Administratorrechte verfügen, um lokale Hilfeinhalte nach der Installation aktualisieren, hinzufügen oder entfernen zu können.  
  
 Zu beachten:  
  
-   Die Hilfe bleibt standardmäßig online gespeichert.  
  
    > [!TIP]
    >  Sie können die standardmäßige Quelle für Hilfe ändern, indem Sie diesen Registrierungsschlüssel ändern: HKEY\_LOCAL\_MACHINE\\Software\\Microsoft\\VisualStudio\\14.0\\help\\UseOnlineHelp.  Weitere Informationen finden Sie unter [Überschreibungen durch den Hilfeinhalts\-Manager](../ide/help-content-manager-overrides.md).  
  
-   Clients werden weiterhin aufgefordert, den grundlegenden Hilfeinhalt beim ersten Start von Visual Studio zu installieren.  Sie können diese Eingabeaufforderung deaktivieren, indem Sie diesen Registrierungsschlüssel ändern: HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Wow6432Node\\Microsoft\\VisualStudio\\14.0\\Help\\DisableFirstRunHelpSelection.  
  
### Beispiel  
 Im folgenden Beispiel werden englische Inhalte für Visual Studio auf einem Clientcomputer installiert.  
  
##### So installieren Sie englische Inhalte über das Internet  
  
1.  Klicken Sie auf **Start** und dann auf **Ausführen**.  
  
2.  Geben Sie folgenden Pfad ein:  
  
     C:\\Program Files \(x86\)\\Microsoft Help Viewer\\v2.2\\hlpctntmgr.exe \/operation install \/catalogname VisualStudio14 \/locale en\-us  
  
3.  Drücken Sie die EINGABETASTE.  
  
## Bereitstellen der vorinstallierten lokalen Hilfeinhalte auf Clientcomputern  
 Sie können Inhalte von einem Onlinespeicherort auf einem Computer installieren und die Inhalte anschließend auf andere Computer kopieren.  
  
 Anforderungen:  
  
-   Der Computer, auf dem Sie den Inhalt installieren, muss mit dem Internet verbunden sein.  
  
-   Benutzer müssen über Administratorrechte verfügen, um lokale Hilfeinhalte nach der Installation aktualisieren, hinzufügen oder entfernen zu können.  
  
    > [!TIP]
    >  Wenn Benutzer nicht über Administratorrechte verfügen, wird empfohlen, die Registerkarte zum Verwalten von Inhalten im Help Viewer zu deaktivieren.  Weitere Informationen finden Sie unter [Überschreibungen durch den Hilfeinhalts\-Manager](../ide/help-content-manager-overrides.md).  
  
 Zu beachten:  
  
-   Wenn Benutzer nicht über Administratorrechte verfügen, wird empfohlen, die Registerkarte zum Verwalten von Inhalten im Help Viewer zu deaktivieren.  Weitere Informationen finden Sie unter [Überschreibungen durch den Hilfeinhalts\-Manager](../ide/help-content-manager-overrides.md).  
  
-   Die Hilfe bleibt standardmäßig online gespeichert.  
  
-   Clients werden weiterhin aufgefordert, den grundlegenden Hilfeinhalt beim ersten Start von Visual Studio zu installieren.  Weitere Informationen finden Sie unter [Überschreibungen durch den Hilfeinhalts\-Manager](../ide/help-content-manager-overrides.md).  
  
### Erstellen der Inhalte  
 Bevor Sie die grundlegenden Inhalte erstellen können, müssen Sie alle lokalen Visual Studio\-Inhalte auf dem Zielcomputer deinstallieren.  
  
##### So deinstallieren Sie die lokale Hilfe  
  
1.  Klicken Sie in Help Viewer auf die Registerkarte **Inhalt verwalten**.  
  
2.  Navigieren Sie unter **Verfügbare Dokumentation** zu den Visual Studio\-Dokumenten.  
  
3.  Wählen Sie **Entfernen** neben den einzelnen Unterelementen aus.  
  
4.  Wählen Sie zum Deinstallieren die Option **Start** aus.  
  
5.  Navigieren Sie zu "*n*:\\ProgramData\\Microsoft\\HelpLibrary2\\Catalogs\\VisualStudio12", und überprüfen Sie, ob der Ordner nur die Datei "catalogType.xml" enthält.  
  
 Nachdem Sie alle zuvor installierten lokalen Visual Studio\-Hilfeinhalte entfernt haben, können Sie die grundlegenden Inhalte herunterladen.  
  
##### So laden Sie die Inhalte herunter  
  
1.  Klicken Sie in Help Viewer auf die Registerkarte **Inhalt verwalten**.  
  
2.  Navigieren Sie unter **Verfügbare Dokumentation** zu den Dokumentationen, die Sie herunterladen möchten, und klicken Sie auf **Hinzufügen**.  
  
3.  Wählen Sie **Start** aus.  
  
 Anschließend müssen Sie den Inhalt so verpacken, dass er auf Clientcomputern bereitgestellt werden kann.  
  
##### So verpacken Sie die Inhalte  
  
1.  Erstellen Sie einen Ordner, um die Inhalte zur späteren Bereitstellung zu kopieren.  
  
     Beispiel: c:\\VS12Help.  
  
2.  Öffnen Sie "cmd.exe" mit Administratorberechtigungen.  
  
3.  Navigieren Sie zu dem in Schritt 1 erstellten Ordner.  
  
4.  Geben Sie folgenden Pfad ein:  
  
     Xcopy %SYSTEMDRIVE%\\ProgramData\\Microsoft\\HelpLibrary2 \<*foldername*\>\\ \/y \/e \/k \/o  
  
     Beispiel: `Xcopy %SYSTEMDRIVE%\ProgramData\Microsoft\HelpLibrary2 c:\VS12Help\ /y /e /k /o`  
  
### Bereitstellen der Inhalte  
  
##### So stellen Sie die Inhalte bereit  
  
1.  Erstellen Sie eine Netzwerkfreigabe und kopieren Sie die Hilfeinhalte an diesen Speicherort.  
  
     Kopieren Sie beispielsweise den Inhalt von "c:\\VS12Help" nach "\\\\myserver\\VS12Help".  
  
2.  Erstellen Sie eine BAT\-Datei für das Bereitstellungsskript für den Hilfeinhalt.  Da auf dem Client eine Lesesperre für die im Rahmen des Push\-Vorgangs gelöschten Dateien eingerichtet sein könnte, sollte der Client heruntergefahren werden, bevor Sie Updates per Push übertragen.  
  
     Beispiel:  
  
    ```  
    REM - copy pre-ripped content to ProgramData  
    Xcopy %~dp0HelpLibrary2 %SYSTEMDRIVE%\ProgramData\Microsoft\HelpLibrary2\ /y /e /k /o  
    if ERRORLEVEL 1 ECHO *** ERROR COPYING Help Library files to Programdata (%ERRORLEVEL%)  
  
    REM - get processor type and create/run registry update file  
    IF "%PROCESSOR_ARCHITECTURE%"=="AMD64" GOTO AMD64  
  
    @echo Architecture type is x86  
  
    ECHO Windows Registry Editor Version 5.00 > x86.reg  
  
    ECHO [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Help\v2.2\Catalogs] >> x86.reg  
    ECHO "ContentStore"="%SYSTEMDRIVE%\\ProgramData\\Microsoft\\HelpLibrary2\\Catalogs\\" >> x86.reg  
  
    ECHO [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Help\v2.2\Catalogs\VisualStudio12] >> x86.reg  
    ECHO "LocationPath"="%SYSTEMDRIVE%\\ProgramData\\Microsoft\\HelpLibrary2\\Catalogs\\VisualStudio12\\"  >> x86.reg  
    ECHO "FirstTimeRun"="False"  >> x86.reg  
  
    ECHO [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Help\v2.2\Catalogs\VisualStudio12\en-US]  >> x86.reg  
    ECHO "ContentStore"="%SYSTEMDRIVE%\\ProgramData\\Microsoft\\HelpLibrary2\\Catalogs\\VisualStudio12\\"  >> x86.reg  
    ECHO "catalogName"="Visual Studio version Help Documentation"  >> x86.reg  
  
    ECHO [HKEY_LOCAL_MACHINE\Software\Microsoft\VSWinExpress\14.0\help]  >> x86.reg  
    ECHO "UseOnlineHelp"=dword:00000000  >> x86.reg  
  
    regedit.exe /s x86.reg  
    if ERRORLEVEL 1 ECHO *** ERROR inserting the x86 reg (%ERRORLEVEL%)  
  
    GOTO CONTINUE  
  
    :AMD64  
    @echo Architecture type is AMD64  
  
    ECHO Windows Registry Editor Version 5.00 > x64.reg  
  
    ECHO [HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\Help\v2.2\Catalogs] >> x64.reg  
    ECHO "ContentStore"="%SYSTEMDRIVE%\\ProgramData\\Microsoft\\HelpLibrary2\\Catalogs\\" >> x64.reg  
  
    ECHO [HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\Help\v2.2\Catalogs\VisualStudio14] >> x64.reg  
    ECHO "LocationPath"="%SYSTEMDRIVE%\\ProgramData\\Microsoft\\HelpLibrary2\\Catalogs\\VisualStudio14\\"  >> x64.reg  
    ECHO "FirstTimeRun"="False"  >> x64.reg  
  
    ECHO [HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\Help\v2.2\Catalogs\VisualStudio14\en-US]  >> x64.reg  
    ECHO "ContentStore"="%SYSTEMDRIVE%\\ProgramData\\Microsoft\\HelpLibrary2\\Catalogs\\VisualStudio12\\en-US\\"  >> x64.reg  
    ECHO "catalogName"="Visual Studio version Help Documentation"  >> x64.reg  
  
    ECHO [HKEY_LOCAL_MACHINE\Software\Wow6432Node\Microsoft\VSWinExpress\14.0\help]  >> x64.reg  
    ECHO "UseOnlineHelp"=dword:00000000  >> x64.reg  
  
    regedit.exe /s x64.reg  
    if ERRORLEVEL 1 ECHO *** ERROR inserting the x64 reg (%ERRORLEVEL%)  
  
    :CONTINUE  
    ```  
  
3.  Führen Sie die BAT\-Datei auf den lokalen Computern aus, auf denen die Hilfeinhalte installiert werden sollen.  
  
## Siehe auch  
 [Befehlszeilenargumente für den Hilfeinhalts\-Manager](../ide/command-line-arguments-for-the-help-content-manager.md)   
 [Überschreibungen durch den Hilfeinhalts\-Manager](../ide/help-content-manager-overrides.md)