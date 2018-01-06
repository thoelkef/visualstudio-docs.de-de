---
title: "Vorgehensweise: erstellen eine Dienstanwendung für WCF-Workflow | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 12d675ac-27d8-4d86-ba16-6f7688f8c841
caps.latest.revision: "14"
author: ErikRe
ms.author: erikre
manager: erikre
ms.workload: multiple
ms.openlocfilehash: 8730b8f1611694ec7927b52fa4118cf3ca3801b7
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-a-wcf-workflow-service-application"></a>Vorgehensweise: Erstellen einer Dienstanwendung für WCF-Workflows
[!INCLUDE[indigo1](../workflow-designer/includes/indigo1_md.md)]-Workflowdienstanwendungen sind verteilte Kommunikationsdienste, die prozessübergreifend Nachrichten zwischen Clients und untereinander übergeben. Die Implementierung des Dienstvertrags auf der Dienstseite erfolgt deklarativ über Workflowaktivitäten in [!INCLUDE[netfx40_short](../workflow-designer/includes/netfx40_short_md.md)], analog zu den früheren Workflowdiensten in .NET Framework 3.5.  
  
### <a name="to-create-a-wcf-workflow-service-application"></a>So erstellen Sie eine WCF-Workflowdienstanwendung  
  
1.  Starten Sie [!INCLUDE[vs2010](../misc/includes/vs2010_md.md)].  
  
2.  Auf der **Datei** Sie im Menü **neu**, und wählen Sie dann **Projekt...** .  
  
     Das Dialogfeld **Neues Projekt** wird angezeigt.  
  
3.  In der **installierte Vorlagen** klicken Sie im Bereich **WCF** oder **Workflow** entweder aus der **Visual C#-** oder **Visual Basic** Gruppierungen je nach bevorzugter Sprache.  
  
4.  Wählen Sie im mittleren Bereich **WCF-Workflowdienstanwendung**.  
  
5.  In der **Namen** Geben Sie einen beschreibenden Namen für das Projekt in der es einfach identifizieren zu können.  
  
6.  In der **Speicherort** Geben Sie das Verzeichnis, in dem Sie das Projekt gespeichert werden soll, oder klicken möchten **Durchsuchen** navigieren.  
  
7.  In der **Lösung** Feld aus, wählen Sie entweder eine neue Projektmappe erstellen, und klicken Sie dann auf **OK**.  
  
    > [!NOTE]
    >  Wenn Sie einer vorhandenen Projektmappe eine workflowkonsolenanwendung hinzufügen möchten, öffnen Sie die Projektmappe in [!INCLUDE[vs2010](../misc/includes/vs2010_md.md)], klicken Sie mit der mit der rechten Maustaste auf die Projektmappe in **Projektmappen-Explorer**, und wählen Sie **hinzufügen**, klicken Sie dann  **Neues Projekt...**  So öffnen die **neues Projekt** (Dialogfeld). Fahren Sie wie oben in dieser Prozedur beschrieben fort.  
  
8.  Die Projektvorlage erstellt eine Dienstdefinition im XAML-Format. Der [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)] wird in der Entwurfsansicht mit einer <xref:System.Activities.Statements.Sequence>-Aktivität geöffnet, die einen Satz von <xref:System.ServiceModel.Activities.Receive>-Aktivitäten und <xref:System.ServiceModel.Activities.SendReply>-Aktivitäten enthält.  
  
## <a name="see-also"></a>Siehe auch  
 [Vorgehensweise: Erstellen Sie eine Aktivität](/dotnet/framework/windows-workflow-foundation/how-to-create-an-activity)   
 [Erstellen eines Workflowprojekts](../workflow-designer/creating-a-workflow-project.md)