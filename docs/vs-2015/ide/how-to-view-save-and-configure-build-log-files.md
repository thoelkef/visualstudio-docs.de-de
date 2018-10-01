---
title: 'Vorgehensweise: Anzeigen, Speichern und Konfigurieren von Buildprotokolldateien | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 75d38b76-26d6-4f43-bbe7-cbacd7cc81e7
caps.latest.revision: 9
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: d30e2b571e0a46afa10c8100085e6c23513159e8
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47523111"
---
# <a name="how-to-view-save-and-configure-build-log-files"></a>Gewusst wie: Anzeigen, Speichern und Konfigurieren von Buildprotokolldateien
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [Vorgehensweise: anzeigen, speichern und Konfigurieren von Buildprotokolldateien](https://docs.microsoft.com/visualstudio/ide/how-to-view-save-and-configure-build-log-files).  
  
Nachdem Sie ein Projekt in der Visual Studio-IDE erstellt haben, werden Informationen zu diesem Build im Fenster **Ausgabe** angezeigt. Anhand dieser Informationen können Sie beispielsweise einen Buildfehler beheben. Bei C++-Projekten werden die gleichen Informationen in einer TXT-Datei angezeigt, die automatisch erstellt und gespeichert wird. Bei Projekten mit verwaltetem Code können Sie die Informationen aus dem Fenster **Ausgabe** kopieren, in eine TXT-Datei kopieren und diese manuell speichern. Sie können die IDE ebenfalls verwenden, um anzugeben, welche Informationen zu jedem Build angezeigt werden sollen.  
  
 Wenn Sie ein Projekt mithilfe von MSBuild erstellen, können Sie eine TXT-Datei erstellen, um Informationen zum Build zu speichern. Weitere Informationen finden Sie unter [Erhalten von Buildprotokollen](../msbuild/obtaining-build-logs-with-msbuild.md).  
  
### <a name="to-view-the-build-log-file-for-a-c-project"></a>Anzeigen der Buildprotokolldatei für ein C++-Projekt  
  
1.  Öffnen Sie im **Windows-Explorer** oder im **Datei-Explorer** folgende Datei: \\...\Visual Studio *Version*\Projekte\\*Projektname*\\*Projektname*\Debug\\*Projektname*.txt.  
  
### <a name="to-create-a-build-log-file-for-a-managed-code-project"></a>Erstellen einer Buildprotokolldatei für ein Projekt mit verwaltetem Code  
  
1.  Wählen Sie in der Menüleiste **Erstellen**, **Projektmappe erstellen**.  
  
2.  Markieren Sie im Fenster **Ausgabe** die Informationen aus dem Build, und kopieren Sie diese in die Zwischenablage.  
  
3.  Öffnen Sie einen Text-Editor wie Editor, fügen Sie die Informationen in die Datei ein, und speichern Sie diese anschließend.  
  
### <a name="to-change-the-amount-of-information-included-in-the-build-log"></a>Ändern der Informationsmenge im Buildprotokoll  
  
1.  Wählen Sie in der Menüleiste **Extras**, **Optionen**.  
  
2.  Klicken Sie auf der Seite **Projekte und Projektmappen** auf **Erstellen und Ausführen**.  
  
3.  Wählen Sie einen der folgenden Werte aus der Liste **Ausführlichkeit der MSBuild-Projektbuildausgabe** aus, und klicken Sie dann auf die Schaltfläche **OK**.  
  
    |Ausführlichkeitsgrad|Beschreibung|  
    |---------------------|-----------------|  
    |Quiet|Zeigt ausschließlich eine Zusammenfassung des Builds an.|  
    |Minimal|Zeigt eine Zusammenfassung des Builds sowie Fehler, Warnungen und Meldungen an, die als äußerst wichtig eingestuft werden.|  
    |Normal|Zeigt eine Zusammenfassung des Builds, die wichtigsten Schritte des Builds sowie Fehler, Warnungen und Meldungen an, die als äußerst wichtig eingestuft werden. Diese Detailebene verwenden Sie am häufigsten.|  
    |Detailliert|Zeigt eine Zusammenfassung des Builds, alle Schritte des Builds sowie Fehler, Warnungen und Meldungen an, die als äußerst wichtig eingestuft werden. Außerdem werden Meldungen von normaler Wichtigkeit angezeigt.|  
    |Diagnose|Zeigt alle Daten an, die für den Build verfügbar sind. Sie können diese Detailebene für das Debuggen von Fehlern bei benutzerdefinierten Buildskripts und anderen Buildfehlern verwenden.|  
  
     Weitere Informationen finden Sie unter [Optionen (Dialogfeld), Projekte und Projektmappen, Erstellen und Ausführen](../ide/reference/options-dialog-box-projects-and-solutions-build-and-run.md) und <xref:Microsoft.Build.Framework.LoggerVerbosity>.  
  
    > [!IMPORTANT]
    >  Sie müssen das Projekt neu erstellen, damit Ihre Änderungen im Fenster **Ausgabe** (alle Projekte) und in der Datei „*Projektname*.txt“ (nur C++-Projekte) wirksam werden.  
  
## <a name="see-also"></a>Siehe auch  
 [Erhalten von Buildprotokollen](../msbuild/obtaining-build-logs-with-msbuild.md)   
 [Erstellen und Bereinigen von Projekten und Projektmappen in Visual Studio](../ide/building-and-cleaning-projects-and-solutions-in-visual-studio.md)   
 [Kompilieren und Erstellen](../ide/compiling-and-building-in-visual-studio.md)



