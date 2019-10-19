---
title: 'Vorgehensweise: Erstellen einer Workflow Aktivitäts Bibliothek (Legacy) | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
helpviewer_keywords:
- workflows, activity library projects
- workflow activity libraries
- projects, workflow activity libraries
ms.assetid: fb5aa940-2ae8-4b52-b52c-51c20861a7b4
caps.latest.revision: 8
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: d5bc4566c1ea520ac1050227ac8e4c0aee22e617
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2019
ms.locfileid: "72604963"
---
# <a name="how-to-create-a-workflow-activity-library-legacy"></a>Vorgehensweise: Erstellen einer Workflowaktivitätsbibliothek (Vorgängerversion)
Führen Sie die folgenden Schritte aus, um ein Projekt für eine Workflowaktivitätsbibliothek mithilfe der Vorgängerversion von [!INCLUDE[wfd1](../includes/wfd1-md.md)] zu erstellen, die von [!INCLUDE[vs2010](../includes/vs2010-md.md)] bereitgestellt wird. Verwenden Sie die Vorgängerversion von [!INCLUDE[wfd2](../includes/wfd2-md.md)], wenn Sie entweder auf [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] oder [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)] abzielen möchten.

### <a name="to-create-a-workflow-activity-library-project"></a>So erstellen Sie ein Workflowaktivitätsbibliothekprojekt

1. Starten Sie Visual Studio.

2. Zeigen Sie im Menü **Datei** auf **Neu**, und klicken Sie dann auf **Projekt**.

     Das Dialogfeld **Neues Projekt** wird angezeigt.

3. Wählen Sie in der Dropdown Liste am oberen Rand des Fensters **Neues Projekt** entweder die Option **.NET Framework 3,0** oder die Option **.NET Framework 3,5** aus, um auf den Legacy-Designer zuzugreifen.

    > [!NOTE]
    > Die Standardoption in [!INCLUDE[vs2010](../includes/vs2010-md.md)] ist **.NET Framework 4**. Diese Option wird zum Erstellen von [!INCLUDE[wf](../includes/wf-md.md)]-Anwendungen verwendet, die auf [!INCLUDE[netfx40_short](../includes/netfx40-short-md.md)] abzielen; dabei wird nicht der Designer der Vorgängerversion verwendet.

4. Wählen Sie im Bereich **Projekttypen** die Option C# Visual oder Visual Basic (unter **andere Sprachen**) aus, und wählen Sie dann **Workflow**aus.

5. Wählen Sie im Bereich **Vorlagen** die Option **Workflow Aktivitäts Bibliothek**aus.

6. Geben Sie im Feld **Name** einen beschreibenden Namen für das Projekt ein, damit es leicht zu erkennen ist.

7. Geben Sie im Feld **Speicherort** das Verzeichnis ein, in dem Sie das Projekt speichern möchten, oder klicken Sie auf **Durchsuchen** , um zu diesem Verzeichnis zu navigieren.

     Wenn Sie ein Projektmappenverzeichnis für das Projekt erstellen möchten, aktivieren Sie das Kontrollkästchen **Projektmappenverzeichnis erstellen** , und geben Sie im Feld Projektmappenname einen Namen ein.

8. Klicken Sie auf **OK**.

## <a name="see-also"></a>Siehe auch
 [Erstellen von Legacy Workflow Projekten](../workflow-designer/creating-legacy-workflow-projects.md) mithilfe der Legacy [Workflow Aktivitäten](../workflow-designer/legacy-workflow-activities.md) [des Legacy Aktivitäts Designers](../workflow-designer/using-the-legacy-activity-designer.md) [entwickeln von Workflow Aktivitäten](https://msdn.microsoft.com/19876dfc-dfa5-4d52-b1f5-1d087474cc52) [Windows Workflow Foundation Aktivitäten](https://msdn.microsoft.com/192c4c1e-afb6-4f58-ab11-2b5bbbc2d2c0)