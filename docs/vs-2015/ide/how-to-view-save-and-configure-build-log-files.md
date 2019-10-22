---
title: 'Vorgehensweise: Anzeigen, Speichern und Konfigurieren von Buildprotokolldateien | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: 75d38b76-26d6-4f43-bbe7-cbacd7cc81e7
caps.latest.revision: 9
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: ffc1c620136c55c42f3468129ed164075d762bff
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2019
ms.locfileid: "72670509"
---
# <a name="how-to-view-save-and-configure-build-log-files"></a>Gewusst wie: Anzeigen, Speichern und Konfigurieren von Buildprotokolldateien
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Nachdem Sie ein Projekt in der Visual Studio-IDE erstellt haben, werden Informationen zu diesem Build im Fenster **Ausgabe** angezeigt. Anhand dieser Informationen können Sie beispielsweise einen Buildfehler beheben. Bei C++-Projekten werden die gleichen Informationen in einer TXT-Datei angezeigt, die automatisch erstellt und gespeichert wird. Bei Projekten mit verwaltetem Code können Sie die Informationen aus dem Fenster **Ausgabe** kopieren, in eine TXT-Datei kopieren und diese manuell speichern. Sie können die IDE ebenfalls verwenden, um anzugeben, welche Informationen zu jedem Build angezeigt werden sollen.

 Wenn Sie ein Projekt mithilfe von MSBuild erstellen, können Sie eine TXT-Datei erstellen, um Informationen zum Build zu speichern. Weitere Informationen finden Sie unter [Erhalten von Buildprotokollen](../msbuild/obtaining-build-logs-with-msbuild.md).

### <a name="to-view-the-build-log-file-for-a-c-project"></a>Anzeigen der Buildprotokolldatei für ein C++-Projekt

1. Öffnen Sie im **Windows-Explorer** oder im **Datei-Explorer** folgende Datei: \\...\Visual Studio *Version*\Projekte\\*Projektname*\\*Projektname*\Debug\\*Projektname*.txt.

### <a name="to-create-a-build-log-file-for-a-managed-code-project"></a>Erstellen einer Buildprotokolldatei für ein Projekt mit verwaltetem Code

1. Wählen Sie in der Menüleiste **Erstellen**, **Projektmappe erstellen**.

2. Markieren Sie im Fenster **Ausgabe** die Informationen aus dem Build, und kopieren Sie diese in die Zwischenablage.

3. Öffnen Sie einen Text-Editor wie Editor, fügen Sie die Informationen in die Datei ein, und speichern Sie diese anschließend.

### <a name="to-change-the-amount-of-information-included-in-the-build-log"></a>Ändern der Informationsmenge im Buildprotokoll

1. Wählen Sie in der Menüleiste **Extras**, **Optionen**.

2. Klicken Sie auf der Seite **Projekte und Projektmappen** auf **Erstellen und Ausführen**.

3. Wählen Sie einen der folgenden Werte aus der Liste **Ausführlichkeit der MSBuild-Projektbuildausgabe** aus, und klicken Sie dann auf die Schaltfläche **OK**.

    |Ausführlichkeitsgrad|BESCHREIBUNG|
    |---------------------|-----------------|
    |Quiet|Zeigt ausschließlich eine Zusammenfassung des Builds an.|
    |Minimal|Zeigt eine Zusammenfassung des Builds sowie Fehler, Warnungen und Meldungen an, die als äußerst wichtig eingestuft werden.|
    |Normal|Zeigt eine Zusammenfassung des Builds, die wichtigsten Schritte des Builds sowie Fehler, Warnungen und Meldungen an, die als äußerst wichtig eingestuft werden. Diese Detailebene verwenden Sie am häufigsten.|
    |Detailliert|Zeigt eine Zusammenfassung des Builds, alle Schritte des Builds sowie Fehler, Warnungen und Meldungen an, die als äußerst wichtig eingestuft werden. Außerdem werden Meldungen von normaler Wichtigkeit angezeigt.|
    |Diagnose|Zeigt alle Daten an, die für den Build verfügbar sind. Sie können diese Detailebene für das Debuggen von Fehlern bei benutzerdefinierten Buildskripts und anderen Buildfehlern verwenden.|

     Weitere Informationen finden Sie unter [Optionen (Dialogfeld), Projekte und Projektmappen, Erstellen und Ausführen](../ide/reference/options-dialog-box-projects-and-solutions-build-and-run.md) und <xref:Microsoft.Build.Framework.LoggerVerbosity>.

    > [!IMPORTANT]
    > Sie müssen das Projekt neu erstellen, damit Ihre Änderungen im Fenster **Ausgabe** (alle Projekte) und in der Datei „*Projektname*.txt“ (nur C++-Projekte) wirksam werden.

## <a name="see-also"></a>Siehe auch
 Abrufen von [buildprotokollen](../msbuild/obtaining-build-logs-with-msbuild.md) erstellen [und Bereinigen von Projekten und Projektmappen in Visual Studio](../ide/building-and-cleaning-projects-and-solutions-in-visual-studio.md) [Kompilieren und erstellen](../ide/compiling-and-building-in-visual-studio.md)
