---
title: "Ereignisprotokollierung f&#252;r Office-L&#246;sungen"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "Office-Anwendungen [Office-Entwicklung in Visual Studio], Ereignisanzeige"
  - "ClickOnce-Bereitstellung [Office-Entwicklung in Visual Studio], Ereignisanzeige"
  - "Bereitstellen von Anwendungen [Office-Entwicklung in Visual Studio], Ereignisanzeige"
  - "Office-Entwicklung in Visual Studio, Ereignisanzeige"
ms.assetid: 31a246fe-ce1c-4f0e-9a21-9cf974c247fe
caps.latest.revision: 33
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 32
---
# Ereignisprotokollierung f&#252;r Office-L&#246;sungen
  Sie können die Ereignisanzeige in Windows verwenden, um Ausnahmemeldungen anzuzeigen, die von [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] aufgezeichnet werden, wenn Sie Office\-Lösungen installieren oder deinstallieren. Sie können diese Meldungen aus der Ereignisprotokollierung verwenden, um Installations\- und Bereitstellungsprobleme zu beheben.  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
## Lesen des Ereignisprotokolls  
 Öffnen Sie die **Ereignisanzeige**, und filtern Sie nach den Ereignissen, die Sie sehen möchten.  
  
#### So lesen Sie das Ereignisprotokoll in Windows Server 2003 und Windows XP  
  
1.  Öffnen Sie in der Systemsteuerung das Hilfsprogramm **Verwaltung**.  
  
2.  Starten Sie **Ereignisanzeige**.  
  
3.  Wählen Sie in der Liste der Ereignisprotokolle den Eintrag **Anwendung** aus.  
  
4.  Klicken Sie im Menü **Ansicht** auf **Filter**.  
  
5.  Wählen Sie in der Liste **Ereignisquelle** den Eintrag **VSTO 4.0** aus.  
  
6.  Geben Sie für Installationsereignisse in das Feld **Ereignis\-ID** den Wert **4096** ein.  
  
7.  Klicken Sie auf **OK**, um die gefilterte Ansicht anzuzeigen.  
  
#### So lesen Sie das Ereignisprotokoll in Windows 7, Windows Vista und Windows Server 2008  
  
1.  Öffnen Sie in der Systemsteuerung das Hilfsprogramm **Verwaltung**.  
  
2.  Starten Sie **Ereignisanzeige**.  
  
3.  Erweitern Sie **Windows\-Protokolle**.  
  
4.  Wählen Sie in der Liste der Ereignisprotokolle den Eintrag **Anwendung** aus.  
  
5.  Klicken Sie im Menü **Aktion** auf **Aktuelles Protokoll filtern**.  
  
6.  Wählen Sie in der Liste **Ereignisquelle** den Eintrag **VSTO 4.0** aus.  
  
7.  Geben Sie für Installationsereignisse in das Feld **Ereignis\-ID** den Wert **4096** ein.  
  
8.  Klicken Sie auf **OK**, um die gefilterte Ansicht anzuzeigen.  
  
 Die Ereignisanzeige enthält die folgenden Informationen:  
  
-   Der Speicherort des Bereitstellungsmanifests für die Projektmappe  
  
-   Eine Meldung, die die Ursache des Fehlers oder der Ausnahme beschreibt  
  
 Über diese Ausnahmemeldungen können Sie den Grund für ein Installationsproblem ermitteln, z. B. ein nicht vertrauenswürdiges Zertifikat, ein nicht vertrauenswürdiger Dokumentspeicherort oder ein ungültiges Bereitstellungsmanifest.  
  
 Nachdem eine Office\-Projektmappe deinstalliert wurde, verbleiben die Ausnahmemeldungen im Ereignisprotokoll.  
  
 Informationen, wie Ausnahmemeldungen angezeigt oder protokolliert werden, wenn eine Office\-Projektmappe ausgeführt wird, finden Sie unter [Debuggen von Office-Projekten](../vsto/debugging-office-projects.md) und [Debuggen von Office-Projekten](../vsto/debugging-office-projects.md).  
  
### Lokalisierung  
 Die Sprache einer Ausnahmemeldung wird durch die Sprache der Visual Studio\-Tools für Office Runtime bestimmt. Wenn auf dem Computer des Endbenutzers z. B. das japanische Language Pack installiert hat, wird die Ausnahmemeldung in Japanisch in das Ereignisprotokoll geschrieben.  
  
## Deaktivieren die Ereignisprotokollierung  
 Standardmäßig wird die Ereignisprotokollierung aktiviert, wenn Sie Office\-Projektmappen installieren oder deinstallieren. Sie können die Ereignisprotokollierung deaktivieren, indem Sie die Umgebungsvariable VSTO\_EVENTLOGDISABLED auf „1“ \(eins\) festlegen.  
  
#### So deaktivieren Sie das Ereignisprotokoll  
  
1.  Öffnen Sie in der Systemsteuerung das Hilfsprogramm **System**.  
  
2.  Klicken Sie auf der Registerkarte **Erweitert** auf **Umgebungsvariablen**.  
  
3.  Klicken Sie im Bereich **Systemvariablen** auf **Neu**.  
  
4.  Geben Sie im Dialogfeld **Neue Systemvariable** in das Feld **Variablenname** den Namen **VSTO\_EVENTLOGDISABLED** ein.  
  
5.  Geben Sie in das Feld **Variablenwert** den Wert **1** ein.  
  
6.  Klicken Sie auf **OK**.  
  
## Siehe auch  
 [Bereitstellen einer Office-Projektmappe](../vsto/deploying-an-office-solution.md)   
 [Problembehandlung bei der Office-Projektmappenbereitstellung](../vsto/troubleshooting-office-solution-deployment.md)  
  
  