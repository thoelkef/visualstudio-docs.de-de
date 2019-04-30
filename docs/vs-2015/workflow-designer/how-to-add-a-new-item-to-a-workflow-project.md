---
title: 'Vorgehensweise: Hinzufügen eines neuen Elements zu einem Workflowprojekt | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
ms.assetid: 5c6180ca-af10-4513-b0cb-7d478fd84eab
caps.latest.revision: 14
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: ecc310896f7b938025d42e06ac5ef0ec8bac3d35
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62932991"
---
# <a name="how-to-add-a-new-item-to-a-workflow-project"></a>Vorgehensweise: Hinzufügen eines neuen Elements zu einem Workflowprojekt
Nach der Erstellung eines Workflowprojekts können Sie diesem Projekt Workflowaktivitäten, Designer und andere bekannte [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]-Elemente hinzufügen.  
  
 In der folgenden Tabelle werden die [!INCLUDE[wf](../includes/wf-md.md)]-Elemente aufgeführt, die Sie einem Workflowprojekt hinzufügen können.  
  
|Name|Beschreibung|  
|----------|-----------------|  
|Aktivität|Eine Aktivität, die aus anderen Aktivitäten besteht. Durch die Auswahl dieses Elements die gleiche XAML-Datei dem Projekt hinzugefügt, die Sie erhalten würden, bei der Auswahl der **Aktivitätsbibliothek** Vorlage für ein neues Projekt. [!INCLUDE[crabout](../includes/crabout-md.md)] In diesem Verfahren finden Sie unter [Vorgehensweise: Erstellen einer Aktivitätsbibliothek](../workflow-designer/how-to-create-an-activity-library.md).|  
|Aktivitätsdesigner|Ein Designer, mit dem die Behandlung einer Aktivität zur Entwurfszeit angepasst wird. Durch die Auswahl dieses Elements die gleichen Dateien dem Projekt hinzugefügt, die Sie erhalten würden, bei der Auswahl der **Aktivitäts-Designerbibliothek** Vorlage für ein neues Projekt. [!INCLUDE[crabout](../includes/crabout-md.md)] In diesem Verfahren finden Sie unter [Vorgehensweise: Erstellen eine Aktivitätsdesignerbibliothek](../workflow-designer/how-to-create-an-activity-designer-library.md).|  
|Codeaktivität|Eine Aktivität mit in Code geschriebener Ausführungslogik. Eine Quellcodedatei mit einer Überschreibung der <xref:System.Activities.CodeActivity.Execute%2A>-Methode wird bereits für Sie generiert.|  
|WCF-Workflowdienst|Ein [!INCLUDE[indigo2](../includes/indigo2-md.md)]-Dienst, der mithilfe von Workflowaktivitäten erstellt wurde. Durch die Auswahl dieses Elements die gleichen Dateien dem Projekt hinzugefügt, die Sie erhalten würden, bei der Auswahl der **WCF-Workflowdienstanwendung** Vorlage für ein neues Projekt. [!INCLUDE[crabout](../includes/crabout-md.md)] In diesem Verfahren finden Sie unter [Vorgehensweise: Erstellen eine Dienstanwendung für WCF-Workflows](../workflow-designer/how-to-create-a-wcf-workflow-service-application.md).|  
  
### <a name="to-add-a-new-item-to-a-workflow-project"></a>So fügen Sie ein neues Element zu einem Workflowprojekt hinzu  
  
1. Auf der **Projekt** Menü klicken Sie auf **neues Element hinzufügen...** .  
  
     Die **Hinzufügen eines neuen Elements** Dialogfeld wird geöffnet.  
  
2. In der **installierte Vorlagen** wählen Sie im Bereich **Workflow** Gruppe.  
  
3. Wählen Sie eines der vier Elemente aus. In der vorherigen Tabelle ist die verfügbare Auswahl aufgeführt.  
  
4. Geben Sie einen geeigneten Namen für das Element in der **Namen** Feld am unteren Rand des Dialogfelds.  
  
5. Klicken Sie auf **hinzufügen** um das Element dem aktuellen Workflowprojekt hinzuzufügen.  
  
## <a name="see-also"></a>Siehe auch  
 [Erstellen eines Workflowprojekts](../workflow-designer/creating-a-workflow-project.md)