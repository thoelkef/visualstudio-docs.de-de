---
title: "Vorgehensweise: Erstellen von Workflowprojekten (Vorgängerversion) | Microsoft Docs"
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- workflow projects, creating
- projects, workflow
ms.assetid: 32299555-662c-469d-a90d-89f4700dc78c
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: dc38c6b323ee06ed9b312811eb892e7654134d05
ms.sourcegitcommit: 37c87118f6f41e832da96f21f6b4cc0cf8fee046
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/12/2018
---
# <a name="how-to-create-workflow-projects-legacy"></a>Vorgehensweise: Erstellen von Workflowprojekten (Vorgängerversion)
Führen Sie die folgenden Schritte aus, um ein [!INCLUDE[wf](../workflow-designer/includes/wf_md.md)]-Projekt zu erstellen, das auf [!INCLUDE[netfx35_long](../workflow-designer/includes/netfx35_long_md.md)] oder [!INCLUDE[vstecwinfx](../workflow-designer/includes/vstecwinfx_md.md)] abzielt. Diese Prozedur verwendet die ältere Windows Workflow-Designer bereitgestellten [!INCLUDE[vs2010](../misc/includes/vs2010_md.md)].

### <a name="to-create-a-workflow-project"></a>So erstellen Sie ein Workflowprojekt

1.  Starten Sie [!INCLUDE[vs_current_long](../misc/includes/vs_current_long_md.md)].

2.  Auf der **Datei** Sie im Menü **neu**, und wählen Sie dann **Projekt**.

     Das Dialogfeld **Neues Projekt** wird angezeigt.

3.  Wählen Sie entweder die **.NET Framework 3.0** Option oder der **.NET Framework 3.5** -Option in der Dropdownliste am oberen Rand der **neues Projekt** Fenster aus, um den Designer der Vorgängerversion zuzugreifen.

    > [!NOTE]
    > Die Standardoption in [!INCLUDE[vs2010](../misc/includes/vs2010_md.md)] ist **.NET Framework 4**. Diese Option wird zum Erstellen von [!INCLUDE[wf](../workflow-designer/includes/wf_md.md)]-Anwendungen verwendet, die auf [!INCLUDE[netfx40_short](../workflow-designer/includes/netfx40_short_md.md)] abzielen; dabei wird nicht der Designer der Vorgängerversion verwendet.

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