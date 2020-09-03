---
title: 'Vorgehensweise: Erstellen von Workflow Projekten (Legacy) | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
helpviewer_keywords:
- workflow projects, creating
- projects, workflow
ms.assetid: 32299555-662c-469d-a90d-89f4700dc78c
caps.latest.revision: 6
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 3cf68c1a28f662bfa4e271d3c402ef1c8946b6f1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "72668678"
---
# <a name="how-to-create-workflow-projects-legacy"></a>Vorgehensweise: Erstellen von Workflowprojekten (Vorgängerversion)
Führen Sie die folgenden Schritte aus, um ein [!INCLUDE[wf](../includes/wf-md.md)]-Projekt zu erstellen, das auf [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] oder [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)] abzielt. In dieser Vorgehensweise wird die Vorgängerversion von [!INCLUDE[wfd1](../includes/wfd1-md.md)] verwendet, die von [!INCLUDE[vs2010](../includes/vs2010-md.md)] bereitgestellt wird.

### <a name="to-create-a-workflow-project"></a>So erstellen Sie ein Workflowprojekt

1. Starten Sie [!INCLUDE[vs_current_long](../includes/vs-current-long-md.md)].

2. Zeigen Sie im Menü **Datei** auf **Neu**, und klicken Sie dann auf **Projekt**.

     Das Dialogfeld **Neues Projekt** wird angezeigt.

3. Wählen Sie in der Dropdown Liste am oberen Rand des Fensters **Neues Projekt** entweder die Option **.NET Framework 3,0** oder die Option **.NET Framework 3,5** aus, um auf den Legacy-Designer zuzugreifen.

    > [!NOTE]
    > Die Standardoption in [!INCLUDE[vs2010](../includes/vs2010-md.md)] ist **.NET Framework 4**. Diese Option wird zum Erstellen von [!INCLUDE[wf](../includes/wf-md.md)]-Anwendungen verwendet, die auf [!INCLUDE[netfx40_short](../includes/netfx40-short-md.md)] abzielen; dabei wird nicht der Designer der Vorgängerversion verwendet.

4. Wählen Sie im Bereich **Projekttypen** die Option Visual c#-Projekte oder Visual Basic Projekte aus, und wählen Sie dann **Workflow**aus.

5. Wählen Sie im Bereich **Vorlagen** eine der installierten Projektvorlagen aus:

    - Konsolenanwendung für sequenzielle Workflows

    - Sequenzielle Workflowbibliothek

    - Workflowaktivitätsbibliothek

    - Konsolenanwendung für Zustandsautomatenworkflows

    - Zustandsautomatenworkflowbibliothek

    - Leeres Workflowprojekt

6. Geben Sie im Feld **Name** einen beschreibenden Namen für das Projekt ein, damit es leicht zu erkennen ist.

7. Geben Sie im Feld **Speicherort** das Verzeichnis ein, in dem Sie das Projekt speichern möchten, oder klicken Sie auf **Durchsuchen** , um zum Verzeichnis zu navigieren.

     Wenn Sie ein Projektmappenverzeichnis für das Projekt erstellen möchten, aktivieren Sie das Kontrollkästchen **Projektmappenverzeichnis erstellen** , und geben Sie im Feld Projektmappenname einen Namen ein. **Solution Name**

8. Klicken Sie auf **OK**.

## <a name="see-also"></a>Weitere Informationen
 [Erstellen von Legacyworkflowprojekten](../workflow-designer/creating-legacy-workflow-projects.md)