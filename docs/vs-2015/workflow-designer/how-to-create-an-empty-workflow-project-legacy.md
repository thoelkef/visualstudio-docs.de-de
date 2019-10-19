---
title: 'Vorgehensweise: Erstellen eines leeren Workflow Projekts (Legacy) | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
helpviewer_keywords:
- projects, empty workflow
- empty workflow projects
- workflows, empty workflow projects
ms.assetid: f81b9cf2-9adb-47a2-936b-cb1851614e19
caps.latest.revision: 5
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: d24baf48f74a7e18ee7bb4922ad989fd8e03a38a
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2019
ms.locfileid: "72662736"
---
# <a name="how-to-create-an-empty-workflow-project-legacy"></a>Vorgehensweise: Erstellen von leeren Workflowprojekten (Vorgängerversion)
Führen Sie die folgenden Schritte aus, um ein leeres Workflowprojekt mithilfe der Vorgängerversion von [!INCLUDE[wfd1](../includes/wfd1-md.md)] zu erstellen, die von [!INCLUDE[vs2010](../includes/vs2010-md.md)] bereitgestellt wird. Verwenden Sie die Vorgängerversion von [!INCLUDE[wfd2](../includes/wfd2-md.md)], wenn Sie entweder auf [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] oder [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)] abzielen möchten.

### <a name="to-create-an-empty-workflow-project"></a>So erstellen Sie ein leeres Workflowprojekt

1. Starten Sie Visual Studio.

2. Zeigen Sie im Menü **Datei** auf **Neu**, und klicken Sie dann auf **Projekt**.

     Das Dialogfeld **Neues Projekt** wird angezeigt.

3. Wählen Sie in der Dropdown Liste am oberen Rand des Fensters **Neues Projekt** entweder die Option **.NET Framework 3,0** oder die Option **.NET Framework 3,5** aus, um auf den Legacy-Designer zuzugreifen.

    > [!NOTE]
    > Die Standardoption in [!INCLUDE[vs2010](../includes/vs2010-md.md)] ist **.NET Framework 4**. Diese Option wird zum Erstellen von [!INCLUDE[wf](../includes/wf-md.md)]-Anwendungen verwendet, die auf [!INCLUDE[netfx40_short](../includes/netfx40-short-md.md)] abzielen; dabei wird nicht der Designer der Vorgängerversion verwendet.

4. Wählen Sie im Bereich **Projekttypen** die Option C# Visual oder Visual Basic (unter **andere Sprachen**) aus, und wählen Sie dann **Workflow**aus.

5. Wählen Sie im Bereich **Vorlagen** die Option **leeres Workflow Projekt**aus.

6. Geben Sie im Feld **Name** einen beschreibenden Namen für das Projekt ein, damit es leicht zu erkennen ist.

7. Geben Sie im Feld **Speicherort** das Verzeichnis ein, in dem Sie das Projekt speichern möchten, oder klicken Sie auf **Durchsuchen** , um zu diesem Verzeichnis zu navigieren.

     Wenn Sie ein Projektmappenverzeichnis für das Projekt erstellen möchten, aktivieren Sie das Kontrollkästchen **Projektmappenverzeichnis erstellen** , und geben Sie im Feld Projektmappenname einen Namen ein.

8. Klicken Sie auf **OK**.

## <a name="see-also"></a>Siehe auch
 [Erstellen von Legacyworkflowprojekten](../workflow-designer/creating-legacy-workflow-projects.md)