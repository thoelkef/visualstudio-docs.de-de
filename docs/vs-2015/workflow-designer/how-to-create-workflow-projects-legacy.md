---
title: 'Vorgehensweise: Erstellen von Workflowprojekten (Vorgängerversion) | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: .net-framework-4.6
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- workflow projects, creating
- projects, workflow
ms.assetid: 32299555-662c-469d-a90d-89f4700dc78c
caps.latest.revision: 6
author: gewarren
ms.author: gewarren
manager: erikre
ms.openlocfilehash: 6fb33b391f05baf91a4c35be0d949f66a885e228
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47524403"
---
# <a name="how-to-create-workflow-projects-legacy"></a>Vorgehensweise: Erstellen von Workflowprojekten (Vorgängerversion)
Führen Sie die folgenden Schritte aus, um ein [!INCLUDE[wf](../includes/wf-md.md)]-Projekt zu erstellen, das auf [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] oder [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)] abzielt. In dieser Vorgehensweise wird die Vorgängerversion von [!INCLUDE[wfd1](../includes/wfd1-md.md)] verwendet, die von [!INCLUDE[vs2010](../includes/vs2010-md.md)] bereitgestellt wird.  
  
### <a name="to-create-a-workflow-project"></a>So erstellen Sie ein Workflowprojekt  
  
1.  Starten Sie [!INCLUDE[vs_current_long](../includes/vs-current-long-md.md)].  
  
2.  Zeigen Sie im Menü **Datei** auf **Neu**, und klicken Sie dann auf **Projekt**.  
  
     Das Dialogfeld **Neues Projekt** wird angezeigt.  
  
3.  Wählen Sie entweder die **.NET Framework 3.0** Option oder die **.NET Framework 3.5** -Option in der Dropdownliste am oberen Rand der **neues Projekt** Fenster aus, um den Designer der Vorgängerversion zuzugreifen.  
  
    > [!NOTE]
    >  Die Standardoption in [!INCLUDE[vs2010](../includes/vs2010-md.md)] ist **.NET Framework 4**. Diese Option wird zum Erstellen von [!INCLUDE[wf](../includes/wf-md.md)]-Anwendungen verwendet, die auf [!INCLUDE[netfx40_short](../includes/netfx40-short-md.md)] abzielen; dabei wird nicht der Designer der Vorgängerversion verwendet.  
  
4.  In der **Projekttypen** Bereich, wählen Sie Visual C#-Projekte oder Visual Basic-Projekte, und wählen Sie dann **Workflow**.  
  
5.  In der **Vorlagen** Bereich, wählen Sie eine der installierten Projektvorlagen:  
  
    -   Konsolenanwendung für sequenzielle Workflows  
  
    -   Sequenzielle Workflowbibliothek  
  
    -   Workflowaktivitätsbibliothek  
  
    -   Konsolenanwendung für Zustandsautomatenworkflows  
  
    -   Zustandsautomatenworkflowbibliothek  
  
    -   Leeres Workflowprojekt  
  
6.  In der **Namen** Geben Sie einen beschreibenden Namen für das Projekt in der es einfach identifizieren zu können.  
  
7.  In der **Speicherort** Geben Sie das Verzeichnis, in dem Sie das Projekt speichern, oder klicken Sie auf möchten **Durchsuchen** , zu dem Verzeichnis zu navigieren.  
  
     Wenn ein Projektmappenverzeichnis für das Projekt erstellt werden sollen, wählen Sie die **Projektmappenverzeichnis erstellen** Kontrollkästchen und geben Sie einen Namen in der **Projektmappenname** Feld.  
  
8.  Klicken Sie auf **OK**.  
  
## <a name="see-also"></a>Siehe auch  
 [Erstellen von Legacyworkflowprojekten](../workflow-designer/creating-legacy-workflow-projects.md)