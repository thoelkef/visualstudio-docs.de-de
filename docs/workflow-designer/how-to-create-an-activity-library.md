---
title: "Vorgehensweise: Erstellen einer Aktivit&#228;tsdesignerbibliothek | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 1eeebe74-7303-4345-8a83-fe37a26bc84b
caps.latest.revision: 12
caps.handback.revision: 12
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
---
# Vorgehensweise: Erstellen einer Aktivit&#228;tsdesignerbibliothek
Benutzerdefinierte Aktivitäten werden verwendet, um bestimmte Geschäftsprozesse in einem Workflow zu modellieren.Die Vorlage Aktivitätsbibliothek in [!INCLUDE[vs2010](../modeling/includes/vs2010_md.md)] wurde bereitgestellt, damit Sie solche benutzerdefinierten Aktivitäten visuell mithilfe von [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)] erstellen können.  
  
### So erstellen Sie eine Workflowaktivitätsbibliothek  
  
1.  Starten Sie [!INCLUDE[vs2010](../modeling/includes/vs2010_md.md)].  
  
2.  Zeigen Sie im Menü **Datei** auf **Neu**, und klicken Sie dann auf **Projekt**.  
  
     Das Dialogfeld **Neues Projekt** wird angezeigt.  
  
3.  Wählen Sie im Bereich **Projekttypen** die Option **Workflow** für **Visual C\#**\-Projekte oder **Visual Basic**\-Gruppierungen aus, abhängig von der bevorzugten Sprache.  
  
4.  Wählen Sie im Bereich **Vorlagen** die Option **Aktivitätsbibliothek** aus.  
  
5.  Geben Sie im Feld **Name** einen beschreibenden Namen für das Projekt ein, um es einfach identifizieren zu können.  
  
6.  Geben Sie im Feld **Speicherort** das Verzeichnis ein, in dem das Projekt gespeichert werden soll, oder klicken Sie auf **Durchsuchen**, um zu dem Verzeichnis zu wechseln.  
  
7.  Geben Sie im Feld **Projektmappe** einen aussagekräftigen Namen für die Projektmappe ein, klicken Sie dann auf **OK**.  
  
    > [!NOTE]
    >  Wenn Sie einer vorhandenen Projektmappe eine Workflowkonsolenanwendung hinzufügen möchten, öffnen Sie diese Projektmappe in [!INCLUDE[vs2010](../modeling/includes/vs2010_md.md)], klicken Sie mit der rechten Maustaste im **Projektmappen\-Explorer** auf die Projektmappe, und wählen Sie **Hinzufügen** und dann **Neues Projekt** aus, um das Dialogfeld **Neues Projekt** zu öffnen.Fahren Sie wie oben in dieser Prozedur beschrieben fort.  
  
8.  Die Projektvorlage erstellt eine Aktivitätsdefinition im XAML\-Format.[!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)] wird geöffnet und zeigt den Canvas für die benutzerdefinierte Aktivität an.  
  
9. Ziehen Sie eine Aktivität aus der **Toolbox** auf die Entwurfsoberfläche, um sie in die benutzerdefinierte Aktivität aufzunehmen.  
  
    > [!CAUTION]
    >  Sie können nur eine untergeordnete Aktivität dem Text der benutzerdefinierten Aktivität hinzufügen. Diese untergeordnete Aktivität kann jedoch eine zusammengesetzte Aktivität sein, z. B. eine <xref:System.Activities.Statements.Sequence>\-Aktivität oder <xref:System.Activities.Statements.Flowchart>\-Aktivität.  
  
## Siehe auch  
 [Vorgehensweise: Erstellen einer Aktivität](../Topic/How%20to:%20Create%20an%20Activity.md)   
 [Erstellen eines Workflowprojekts](../workflow-designer/creating-a-workflow-project.md)