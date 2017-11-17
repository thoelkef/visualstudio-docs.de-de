---
title: "Vorgehensweise: Hinzufügen eines neuen Elements zu einem Workflowprojekt | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 5c6180ca-af10-4513-b0cb-7d478fd84eab
caps.latest.revision: "14"
author: ErikRe
ms.author: erikre
manager: erikre
ms.openlocfilehash: f748ce8ad7469d88ad2b50eb1704a8b979c1c636
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="how-to-add-a-new-item-to-a-workflow-project"></a>Gewusst wie: Hinzufügen eines neuen Elements zu einem Workflowprojekt
Nach der Erstellung eines Workflowprojekts können Sie diesem Projekt Workflowaktivitäten, Designer und andere bekannte [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]-Elemente hinzufügen.  
  
 In der folgenden Tabelle werden die [!INCLUDE[wf](../workflow-designer/includes/wf_md.md)]-Elemente aufgeführt, die Sie einem Workflowprojekt hinzufügen können.  
  
|Name|Beschreibung|  
|----------|-----------------|  
|Aktivität|Eine Aktivität, die aus anderen Aktivitäten besteht. Durch die Auswahl dieses Elements die gleiche XAML-Datei dem Projekt hinzugefügt, die Sie erhalten würden, bei der Auswahl der **Aktivitätsbibliothek** Vorlage für ein neues Projekt. [!INCLUDE[crabout](../test/includes/crabout_md.md)]für diese Prozedur finden Sie unter [Vorgehensweise: Erstellen einer Aktivitätsdesignerbibliothek](../workflow-designer/how-to-create-an-activity-library.md).|  
|Aktivitätsdesigner|Ein Designer, mit dem die Behandlung einer Aktivität zur Entwurfszeit angepasst wird. Durch die Auswahl dieses Elements die gleichen Dateien, die dem Projekt hinzugefügt, die Sie erhalten würden, bei der Auswahl der **Aktivitätsdesignerbibliothek** Vorlage für ein neues Projekt. [!INCLUDE[crabout](../test/includes/crabout_md.md)]für diese Prozedur finden Sie unter [Vorgehensweise: Erstellen einer Aktivitätsdesignerbibliothek](../workflow-designer/how-to-create-an-activity-designer-library.md).|  
|Codeaktivität|Eine Aktivität mit in Code geschriebener Ausführungslogik. Eine Quellcodedatei mit einer Überschreibung der <xref:System.Activities.CodeActivity.Execute%2A>-Methode wird bereits für Sie generiert.|  
|WCF-Workflowdienst|Ein [!INCLUDE[indigo2](../workflow-designer/includes/indigo2_md.md)]-Dienst, der mithilfe von Workflowaktivitäten erstellt wurde. Durch die Auswahl dieses Elements die gleichen Dateien, die dem Projekt hinzugefügt, die Sie erhalten würden, bei der Auswahl der **WCF-Workflowdienstanwendung** Vorlage für ein neues Projekt. [!INCLUDE[crabout](../test/includes/crabout_md.md)]für diese Prozedur finden Sie unter [Vorgehensweise: Erstellen einer Dienstanwendung für WCF-Workflow](../workflow-designer/how-to-create-a-wcf-workflow-service-application.md).|  
  
### <a name="to-add-a-new-item-to-a-workflow-project"></a>So fügen Sie ein neues Element zu einem Workflowprojekt hinzu  
  
1.  Auf der **Projekt** Menü klicken Sie auf **neues Element hinzufügen...** .  
  
     Die **Hinzufügen eines neuen Elements** Dialogfeld wird geöffnet.  
  
2.  In der **installierte Vorlagen** klicken Sie im Bereich **Workflow** Gruppe.  
  
3.  Wählen Sie eines der vier Elemente aus. In der vorherigen Tabelle ist die verfügbare Auswahl aufgeführt.  
  
4.  Geben Sie einen geeigneten Namen für das Element in der **Namen** Feld am unteren Rand des Dialogfelds.  
  
5.  Klicken Sie auf **hinzufügen** um das Element dem aktuellen Workflowprojekt hinzuzufügen.  
  
## <a name="see-also"></a>Siehe auch  
 [Erstellen eines Workflowprojekts](../workflow-designer/creating-a-workflow-project.md)