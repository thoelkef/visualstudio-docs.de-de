---
title: 'Workflow-Designer - Vorgehensweise: Erstellen von Workflowprojekten (Vorgängerversion)'
ms.date: 11/04/2016
ms.topic: conceptual
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
helpviewer_keywords:
- workflow projects, creating
- projects, workflow
ms.assetid: 32299555-662c-469d-a90d-89f4700dc78c
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: bb5d58c6d450a5e68d804e33785ec76349bfb6d8
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-create-workflow-projects-legacy"></a>Vorgehensweise: Erstellen von Workflowprojekten (Vorgängerversion)

Führen Sie diese Schritte aus, um ein Windows Workflow Foundation (WF)-Projekt erstellen, die auf .NET Framework, Version 3.5 oder die WinFX ausgerichtet ist. Diese Prozedur verwendet die älteren Windows-Workflow-Designer von Visual Studio 2010 bereitgestellt.

## <a name="to-create-a-workflow-project"></a>So erstellen Sie ein Workflowprojekt

1.  Starten Sie Visual Studio.

2.  Zeigen Sie im Menü **Datei** auf **Neu**, und klicken Sie dann auf **Projekt**.

     Das Dialogfeld **Neues Projekt** wird angezeigt.

3.  Wählen Sie entweder die **.NET Framework 3.0** Option oder der **.NET Framework 3.5** -Option in der Dropdownliste am oberen Rand der **neues Projekt** Fenster aus, um den Designer der Vorgängerversion zuzugreifen.

    > [!NOTE]
    > Ist die Standardoption in Visual Studio 2010 **.NET Framework 4**. Diese Option dient zum Erstellen von Windows Workflow Foundation (WF)-Anwendungen, die auf .NET Framework 4 abzielen, und es werden keine der Designer den Vorgängerversion verwendet.

4.  In der **Projekttypen** Bereich auswählen, Visual C#-Projekte oder Visual Basic-Projekte, und wählen Sie dann **Workflow**.

5.  In der **Vorlagen** Bereich, wählen Sie eine der installierten Projektvorlagen:

    -   Konsolenanwendung für sequenzielle Workflows

    -   Sequenzielle Workflowbibliothek

    -   Workflowaktivitätsbibliothek

    -   Konsolenanwendung für Zustandsautomatenworkflows

    -   Zustandsautomatenworkflowbibliothek

    -   Leeres Workflowprojekt

6.  In der **Namen** Geben Sie einen beschreibenden Namen für das Projekt in der es einfach identifizieren zu können.

7.  In der **Speicherort** Geben Sie das Verzeichnis, in dem Sie das Projekt gespeichert werden soll, oder klicken möchten **Durchsuchen** in das Verzeichnis zu navigieren.

     Wenn Sie ein Projektmappenverzeichnis für das Projekt erstellt werden soll, wählen Sie die **Projektmappenverzeichnis erstellen** Kontrollkästchen und geben Sie einen Namen in der **Projektmappenname** Feld.

8.  Klicken Sie auf **OK**.

## <a name="see-also"></a>Siehe auch

- [Erstellen von Legacyworkflowprojekten](../workflow-designer/creating-legacy-workflow-projects.md)