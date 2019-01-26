---
title: Ereignisprotokollierung für Office-Projektmappen
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office applications [Office development in Visual Studio], event viewer
- ClickOnce deployment [Office development in Visual Studio], event viewer
- deploying applications [Office development in Visual Studio], event viewer
- Office development in Visual Studio, event viewer
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 029a4390036474d651f9e23becbb3660f097ed13
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/24/2019
ms.locfileid: "54867662"
---
# <a name="event-logging-for-office-solutions"></a>Ereignisprotokollierung für Office-Projektmappen
  Sie können die Ereignisanzeige in Windows verwenden, um Ausnahmemeldungen anzuzeigen, die von [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] aufgezeichnet werden, wenn Sie Office-Lösungen installieren oder deinstallieren. Sie können diese Meldungen aus der Ereignisprotokollierung verwenden, um Installations- und Bereitstellungsprobleme zu beheben.  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
## <a name="read-the-event-log"></a>Lesen Sie das Ereignisprotokoll  
 Öffnen Sie die **Ereignisanzeige** , und filtern Sie nach den Ereignissen, die Sie sehen möchten.  
  
### <a name="to-read-the-event-log-in-windows-server-2003-and-windows-xp"></a>Lesen Sie das Ereignisprotokoll in Windows Server 2003 und Windows XP  
  
1.  Öffnen Sie in der Systemsteuerung das Hilfsprogramm **Verwaltung**.  
  
2.  Starten Sie **Ereignisanzeige**.  
  
3.  Wählen Sie in der Liste der Ereignisprotokolle den Eintrag **Anwendung**aus.  
  
4.  Klicken Sie im Menü **Ansicht** auf **Filter**.  
  
5.  Wählen Sie in der Liste **Ereignisquelle** den Eintrag **VSTO 4.0**aus.  
  
6.  Geben Sie für Installationsereignisse in das Feld **Ereignis-ID** den Wert **4096**ein.  
  
7.  Klicken Sie auf **OK** , um die gefilterte Ansicht anzuzeigen.  
  
### <a name="to-read-the-event-log-in-windows-7-windows-vista-and-windows-server-2008"></a>Lesen Sie das Ereignisprotokoll in Windows 7, Windows Vista und Windows Server 2008  
  
1. Öffnen Sie in der Systemsteuerung das Hilfsprogramm **Verwaltung**.  
  
2. Starten Sie **Ereignisanzeige**.  
  
3. Erweitern Sie **Windows-Protokolle**.  
  
4. Wählen Sie in der Liste der Ereignisprotokolle den Eintrag **Anwendung**aus.  
  
5. Klicken Sie im Menü **Aktion** auf **Aktuelles Protokoll filtern**.  
  
6. Wählen Sie in der Liste **Ereignisquelle** den Eintrag **VSTO 4.0**aus.  
  
7. Geben Sie für Installationsereignisse in das Feld **Ereignis-ID** den Wert **4096**ein.  
  
8. Klicken Sie auf **OK** , um die gefilterte Ansicht anzuzeigen.  
  
   Die Ereignisanzeige enthält die folgenden Informationen:  
  
- Der Speicherort des Bereitstellungsmanifests für die Projektmappe  
  
- Eine Meldung, die die Ursache des Fehlers oder der Ausnahme beschreibt  
  
  Über diese Ausnahmemeldungen können Sie den Grund für ein Installationsproblem ermitteln, z. B. ein nicht vertrauenswürdiges Zertifikat, ein nicht vertrauenswürdiger Dokumentspeicherort oder ein ungültiges Bereitstellungsmanifest.  
  
  Nachdem eine Office-Projektmappe deinstalliert wurde, verbleiben die Ausnahmemeldungen im Ereignisprotokoll.  
  
  Um anzuzeigen, oder melden Sie ausnahmemeldungen, wenn eine Office-Projektmappe ausgeführt wird, finden Sie unter [Debuggen von Office-Projekten](../vsto/debugging-office-projects.md) und [Debuggen von Office-Projekten](../vsto/debugging-office-projects.md).  
  
### <a name="localization"></a>Lokalisierung  
 Die Sprache einer Ausnahmemeldung wird durch die Sprache der Visual Studio-Tools für Office Runtime bestimmt. Wenn es sich bei der Computer des Endbenutzers das japanische Sprachpaket installiert hat, ist die Ausnahmemeldung z. B. in das Ereignisprotokoll in japanischer Sprache geschrieben.  
  
## <a name="disable-the-event-logger"></a>Die ereignisprotokollierung deaktivieren  
 Standardmäßig wird die Ereignisprotokollierung aktiviert, wenn Sie Office-Projektmappen installieren oder deinstallieren. Sie können die Ereignisprotokollierung deaktivieren, indem Sie die Umgebungsvariable VSTO_EVENTLOGDISABLED auf „1“ (eins) festlegen.  
  
### <a name="to-disable-the-event-log"></a>So deaktivieren Sie das Ereignisprotokoll  
  
1.  Öffnen Sie in der Systemsteuerung das Hilfsprogramm **System**.  
  
2.  Klicken Sie auf der Registerkarte **Erweitert** auf **Umgebungsvariablen**.  
  
3.  Klicken Sie im Bereich **Systemvariablen** auf **Neu**.  
  
4.  Geben Sie im Dialogfeld **Neue Systemvariable** in das Feld **Variablenname** den Namen **VSTO_EVENTLOGDISABLED** ein.  
  
5.  Geben Sie in das Feld **Variablenwert** den Wert **1**ein.  
  
6.  Klicken Sie auf **OK**.  
  
## <a name="see-also"></a>Siehe auch  
 [Bereitstellen einer Office-Projektmappe](../vsto/deploying-an-office-solution.md)   
 [Problembehandlung bei Office-projektmappenbereitstellung](../vsto/troubleshooting-office-solution-deployment.md)  
