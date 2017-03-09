---
title: "Vorgehensweise: Erstellen einer Dienstanwendung f&#252;r WCF-Workflows | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 12d675ac-27d8-4d86-ba16-6f7688f8c841
caps.latest.revision: 14
caps.handback.revision: 14
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
---
# Vorgehensweise: Erstellen einer Dienstanwendung f&#252;r WCF-Workflows
[!INCLUDE[indigo1](../workflow-designer/includes/indigo1_md.md)]\-Workflowdienstanwendungen sind verteilte Kommunikationsdienste, die prozessübergreifend Nachrichten zwischen Clients und untereinander übergeben.Die Implementierung des Dienstvertrags auf der Dienstseite erfolgt deklarativ über Workflowaktivitäten in [!INCLUDE[netfx40_short](../workflow-designer/includes/netfx40_short_md.md)], analog zu den früheren Workflowdiensten in .NET Framework 3.5.  
  
### So erstellen Sie eine WCF\-Workflowdienstanwendung  
  
1.  Starten Sie [!INCLUDE[vs2010](../modeling/includes/vs2010_md.md)].  
  
2.  Zeigen Sie im Menü **Datei** auf **Neu**, und klicken Sie dann auf **Projekt**.  
  
     Das Dialogfeld **Neues Projekt** wird angezeigt.  
  
3.  Wählen Sie im Bereich **Installierte Vorlagen** die Option **WCF** oder **Workflow** aus der **Visual C\#**\- oder **Visual Basic**\-Gruppe \(je nach bevorzugter Sprache\) aus.  
  
4.  Wählen Sie im mittleren Bereich **WCF\-Workflowdienstanwendung**.  
  
5.  Geben Sie im Feld **Name** einen beschreibenden Namen für das Projekt ein, um es einfach identifizieren zu können.  
  
6.  Geben Sie im Feld **Speicherort** das Verzeichnis ein, in dem das Projekt gespeichert werden soll, oder klicken Sie auf **Durchsuchen**, um zu dem Verzeichnis zu navigieren.  
  
7.  Wählen Sie im Feld **Projektmappe** aus, ob eine neue Projektmappe erstellt werden soll, und klicken Sie dann auf **OK**.  
  
    > [!NOTE]
    >  Wenn Sie einer vorhandenen Projektmappe eine Workflowkonsolenanwendung hinzufügen möchten, öffnen Sie diese Projektmappe in [!INCLUDE[vs2010](../modeling/includes/vs2010_md.md)], klicken Sie mit der rechten Maustaste im **Projektmappen\-Explorer** auf die Projektmappe, und wählen Sie **Hinzufügen** und dann **Neues Projekt** aus, um das Dialogfeld **Neues Projekt** zu öffnen.Fahren Sie wie oben in dieser Prozedur beschrieben fort.  
  
8.  Die Projektvorlage erstellt eine Dienstdefinition im XAML\-Format.Der [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)] wird in der Entwurfsansicht mit einer <xref:System.Activities.Statements.Sequence>\-Aktivität geöffnet, die einen Satz von <xref:System.ServiceModel.Activities.Receive>\-Aktivitäten und <xref:System.ServiceModel.Activities.SendReply>\-Aktivitäten enthält.  
  
## Siehe auch  
 [Vorgehensweise: Erstellen einer Aktivität](../Topic/How%20to:%20Create%20an%20Activity.md)   
 [Erstellen eines Workflowprojekts](../workflow-designer/creating-a-workflow-project.md)