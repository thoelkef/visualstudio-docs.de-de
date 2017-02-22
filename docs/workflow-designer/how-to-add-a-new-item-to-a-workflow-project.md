---
title: "Gewusst wie: Hinzuf&#252;gen eines neuen Elements zu einem Workflowprojekt | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 5c6180ca-af10-4513-b0cb-7d478fd84eab
caps.latest.revision: 14
caps.handback.revision: 14
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
---
# Gewusst wie: Hinzuf&#252;gen eines neuen Elements zu einem Workflowprojekt
Nach der Erstellung eines Workflowprojekts können Sie diesem Projekt Workflowaktivitäten, Designer und andere bekannte [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]\-Elemente hinzufügen.  
  
 In der folgenden Tabelle werden die [!INCLUDE[wf](../workflow-designer/includes/wf_md.md)]\-Elemente aufgeführt, die Sie einem Workflowprojekt hinzufügen können.  
  
|Name|Beschreibung|  
|----------|------------------|  
|Aktivität|Eine Aktivität, die aus anderen Aktivitäten besteht.Durch die Auswahl dieses Elements wird dem Projekt die gleiche XAML\-Datei hinzugefügt wie beim Auswählen der Vorlage **Aktivitätsbibliothek** für ein neues Projekt.[!INCLUDE[crabout](../test/includes/crabout_md.md)] zu dieser Vorgehensweise erhalten Sie unter [Vorgehensweise: Erstellen einer Aktivitätsdesignerbibliothek](../workflow-designer/how-to-create-an-activity-library.md).|  
|Aktivitätsdesigner|Ein Designer, mit dem die Behandlung einer Aktivität zur Entwurfszeit angepasst wird.Durch die Auswahl dieses Elements werden dem Projekt die gleichen Dateien hinzugefügt wie beim Auswählen der Vorlage **Aktivitätsdesignerbibliothek** für ein neues Projekt.[!INCLUDE[crabout](../test/includes/crabout_md.md)] zu dieser Vorgehensweise erhalten Sie unter [Vorgehensweise: Erstellen einer Aktivitätsdesignerbibliothek](../workflow-designer/how-to-create-an-activity-designer-library.md).|  
|Codeaktivität|Eine Aktivität mit in Code geschriebener Ausführungslogik.Eine Quellcodedatei mit einer Überschreibung der <xref:System.Activities.CodeActivity.Execute%2A>\-Methode wird bereits für Sie generiert.|  
|WCF\-Workflowdienst|Ein [!INCLUDE[indigo2](../workflow-designer/includes/indigo2_md.md)]\-Dienst, der mithilfe von Workflowaktivitäten erstellt wurde.Durch die Auswahl dieses Elements werden dem Projekt die gleichen Dateien hinzugefügt wie beim Auswählen der Vorlage **WCF\-Workflowdienstanwendung** für ein neues Projekt.[!INCLUDE[crabout](../test/includes/crabout_md.md)] zu dieser Vorgehensweise erhalten Sie unter [Vorgehensweise: Erstellen einer Dienstanwendung für WCF\-Workflows](../workflow-designer/how-to-create-a-wcf-workflow-service-application.md).|  
  
### So fügen Sie ein neues Element zu einem Workflowprojekt hinzu  
  
1.  Klicken Sie im Menü **Projekt** auf **Neues Element hinzufügen**.  
  
     Das Dialogfeld **Neues Element hinzufügen** wird angezeigt.  
  
2.  Wählen Sie im Bereich **Installierte Vorlagen** die Gruppe **Workflow** aus.  
  
3.  Wählen Sie eines der vier Elemente aus.In der vorherigen Tabelle ist die verfügbare Auswahl aufgeführt.  
  
4.  Geben Sie im Feld **Name** im unteren Bereich des Dialogfelds einen passenden Namen für das Element ein.  
  
5.  Klicken Sie auf **Hinzufügen**, um das Element dem aktuellen Workflowprojekt hinzuzufügen.  
  
## Siehe auch  
 [Erstellen eines Workflowprojekts](../workflow-designer/creating-a-workflow-project.md)