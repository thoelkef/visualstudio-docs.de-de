---
title: "Vorgehensweise: erstellen eine Workflowaktivitätsbibliothek (Vorgängerversion) | Microsoft Docs"
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- workflows, activity library projects
- workflow activity libraries
- projects, workflow activity libraries
ms.assetid: fb5aa940-2ae8-4b52-b52c-51c20861a7b4
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 60d6fb1aebc6810a271eda8806fe6ac83060f73f
ms.sourcegitcommit: 37c87118f6f41e832da96f21f6b4cc0cf8fee046
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/12/2018
---
# <a name="how-to-create-a-workflow-activity-library-legacy"></a>Vorgehensweise: Erstellen einer Workflowaktivitätsbibliothek (Vorgängerversion)

Befolgen Sie diese Schritte zum Erstellen eines Workflowaktivitätsbibliothek-Projekts mit älteren Windows Workflow-Designer bereitgestellten [!INCLUDE[vs2010](../misc/includes/vs2010_md.md)]. Verwenden Sie die Vorgängerversion von [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)], wenn Sie entweder auf [!INCLUDE[netfx35_long](../workflow-designer/includes/netfx35_long_md.md)] oder [!INCLUDE[vstecwinfx](../workflow-designer/includes/vstecwinfx_md.md)] abzielen möchten.

### <a name="to-create-a-workflow-activity-library-project"></a>So erstellen Sie ein Workflowaktivitätsbibliothekprojekt

1.  Starten Sie Visual Studio.

2.  Auf der **Datei** Sie im Menü **neu**, und wählen Sie dann **Projekt**.

     Das Dialogfeld **Neues Projekt** wird angezeigt.

3.  Wählen Sie entweder die **.NET Framework 3.0** Option oder der **.NET Framework 3.5** -Option in der Dropdownliste am oberen Rand der **neues Projekt** Fenster aus, um den Designer der Vorgängerversion zuzugreifen.

    > [!NOTE]
    > Die Standardoption in [!INCLUDE[vs2010](../misc/includes/vs2010_md.md)] ist **.NET Framework 4**. Diese Option wird zum Erstellen von [!INCLUDE[wf](../workflow-designer/includes/wf_md.md)]-Anwendungen verwendet, die auf [!INCLUDE[netfx40_short](../workflow-designer/includes/netfx40_short_md.md)] abzielen; dabei wird nicht der Designer der Vorgängerversion verwendet.

4.  In der **Projekttypen** Bereich, die Option Visual c# oder Visual Basic (unter **andere Sprachen**) und wählen Sie dann **Workflow**.

5.  In der **Vorlagen** klicken Sie im Bereich **Workflowaktivitätsbibliothek**.

6.  In der **Namen** Geben Sie einen beschreibenden Namen für das Projekt in der es einfach identifizieren zu können.

7.  In der **Speicherort** Geben Sie das Verzeichnis, in dem Sie das Projekt gespeichert werden soll, oder klicken möchten **Durchsuchen** navigieren.

     Wenn Sie ein Projektmappenverzeichnis für das Projekt erstellt werden soll, wählen Sie die **Projektmappenverzeichnis erstellen** Kontrollkästchen und geben Sie einen Namen in der **Projektmappenname** Feld.

8.  Klicken Sie auf **OK**.

## <a name="see-also"></a>Siehe auch

- [Erstellen von Legacyworkflowprojekten](../workflow-designer/creating-legacy-workflow-projects.md)
- [Verwenden des Aktivitätsdesigners der Vorgängerversion](../workflow-designer/using-the-legacy-activity-designer.md)
- [Legacyworkflowaktivitäten](../workflow-designer/legacy-workflow-activities.md)
- [Entwickeln von Workflowaktivitäten](http://msdn.microsoft.com/en-us/19876dfc-dfa5-4d52-b1f5-1d087474cc52)
- [Windows Workflow Foundation-Aktivitäten](http://msdn.microsoft.com/en-us/192c4c1e-afb6-4f58-ab11-2b5bbbc2d2c0)