---
title: 'Vorgehensweise: Erstellen einer sequenziellen Workflow Bibliothek (Legacy) | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
helpviewer_keywords:
- sequential workflows, creating library
- workflows, sequential workflow library
- projects, sequential workflow library
- sequential workflow libraries
ms.assetid: 9433ccf3-1eab-4d53-90ff-2e7b2341676c
caps.latest.revision: 5
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: adc2e71678e6892d12640a3153f24bfb90dfa429
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "72663399"
---
# <a name="how-to-create-a-sequential-workflow-library-legacy"></a>Vorgehensweise: Erstellen einer sequenziellen Workflowbibliothek (Vorgängerversion)
Führen Sie die folgenden Schritte aus, um ein Projekt für eine sequenzielle Workflowbibliothek mithilfe der Vorgängerversion von [!INCLUDE[wfd1](../includes/wfd1-md.md)] zu erstellen, die von [!INCLUDE[vs2010](../includes/vs2010-md.md)] bereitgestellt wird. Verwenden Sie die Vorgängerversion von [!INCLUDE[wfd2](../includes/wfd2-md.md)], wenn Sie entweder auf [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] oder [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)] abzielen möchten.

### <a name="to-create-a-sequential-workflow-library-project"></a>So erstellen Sie ein sequenzielles Workflowbibliothekprojekt

1. Starten Sie Visual Studio.

2. Zeigen Sie im Menü **Datei** auf **Neu**, und klicken Sie dann auf **Projekt**.

     Das Dialogfeld **Neues Projekt** wird angezeigt.

3. Wählen Sie in der Dropdown Liste am oberen Rand des Fensters **Neues Projekt** entweder die Option **.NET Framework 3,0** oder die Option **.NET Framework 3,5** aus, um auf den Legacy-Designer zuzugreifen.

    > [!NOTE]
    > Die Standardoption in [!INCLUDE[vs2010](../includes/vs2010-md.md)] ist **.NET Framework 4**. Diese Option wird zum Erstellen von [!INCLUDE[wf](../includes/wf-md.md)]-Anwendungen verwendet, die auf [!INCLUDE[netfx40_short](../includes/netfx40-short-md.md)] abzielen; dabei wird nicht der Designer der Vorgängerversion verwendet.

4. Wählen Sie im Bereich **Projekttypen** die Option Visual c# oder Visual Basic (unter **andere Sprachen**) aus, und wählen Sie dann **Workflow**aus.

5. Wählen Sie im Bereich **Vorlagen** die Option **sequenzielle Workflow Bibliothek**aus.

6. Geben Sie im Feld **Name** einen beschreibenden Namen für das Projekt ein, damit es leicht zu erkennen ist.

7. Geben Sie im Feld **Speicherort** das Verzeichnis ein, in dem Sie das Projekt speichern möchten, oder klicken Sie auf **Durchsuchen** , um zu diesem Verzeichnis zu navigieren.

     Wenn Sie ein Projektmappenverzeichnis für das Projekt erstellen möchten, aktivieren Sie das Kontrollkästchen **Projektmappenverzeichnis erstellen** , und geben Sie im Feld Projektmappenname einen Namen ein. **Solution Name**

8. Klicken Sie auf **OK**.

## <a name="see-also"></a>Weitere Informationen
 Erstellen von Workflow Erstellungs [Stilen](https://msdn.microsoft.com/aacf4ec6-da05-4974-958a-974769dda739) für [Legacy Workflow Projekte](../workflow-designer/creating-legacy-workflow-projects.md)