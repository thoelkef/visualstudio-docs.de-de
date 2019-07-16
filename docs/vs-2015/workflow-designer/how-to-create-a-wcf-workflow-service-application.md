---
title: 'Vorgehensweise: Erstellen eine Dienstanwendung für WCF-Workflows | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
ms.assetid: 12d675ac-27d8-4d86-ba16-6f7688f8c841
caps.latest.revision: 14
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: d0c258ea081e95179c507f76413ae2a5fc7d71a5
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/15/2019
ms.locfileid: "65705853"
---
# <a name="how-to-create-a-wcf-workflow-service-application"></a>Vorgehensweise: Erstellen einer Dienstanwendung für WCF-Workflows
[!INCLUDE[indigo1](../includes/indigo1-md.md)]-Workflowdienstanwendungen sind verteilte Kommunikationsdienste, die prozessübergreifend Nachrichten zwischen Clients und untereinander übergeben. Die Implementierung des Dienstvertrags auf der Dienstseite erfolgt deklarativ über Workflowaktivitäten in [!INCLUDE[netfx40_short](../includes/netfx40-short-md.md)], analog zu den früheren Workflowdiensten in .NET Framework 3.5.  
  
### <a name="to-create-a-wcf-workflow-service-application"></a>So erstellen Sie eine WCF-Workflowdienstanwendung  
  
1. Starten Sie [!INCLUDE[vs2010](../includes/vs2010-md.md)].  
  
2. Auf der **Datei** Startmenü **neu**, und wählen Sie dann **Projekt...** .  
  
     Das Dialogfeld **Neues Projekt** wird angezeigt.  
  
3. In der **installierte Vorlagen** wählen Sie im Bereich **WCF** oder **Workflow** entweder die **Visual C#-** oder **Visual Basic** Gruppierungen je nach bevorzugter Sprache.  
  
4. Wählen Sie im mittleren Bereich **WCF-Workflowdienstanwendung**.  
  
5. In der **Namen** Geben Sie einen beschreibenden Namen für das Projekt in der es einfach identifizieren zu können.  
  
6. In der **Speicherort** Geben Sie das Verzeichnis, in dem Sie das Projekt speichern, oder klicken Sie auf möchten **Durchsuchen** dorthin navigieren.  
  
7. In der **Lösung** Feld aus, wählen Sie entweder eine neue Projektmappe erstellen, und klicken Sie dann auf **OK**.  
  
    > [!NOTE]
    > Wenn Sie einer vorhandenen Projektmappe eine workflowkonsolenanwendung hinzufügen möchten, öffnen Sie die Projektmappe in [!INCLUDE[vs2010](../includes/vs2010-md.md)], klicken Sie mit der rechten Maustaste auf die Projektmappe in **Projektmappen-Explorer**, und wählen Sie **hinzufügen**, klicken Sie dann  **Neues Projekt...** zum Öffnen der **neues Projekt** Dialogfeld. Fahren Sie wie oben in dieser Prozedur beschrieben fort.  
  
8. Die Projektvorlage erstellt eine Dienstdefinition im XAML-Format. Der [!INCLUDE[wfd1](../includes/wfd1-md.md)] wird in der Entwurfsansicht mit einer <xref:System.Activities.Statements.Sequence>-Aktivität geöffnet, die einen Satz von <xref:System.ServiceModel.Activities.Receive>-Aktivitäten und <xref:System.ServiceModel.Activities.SendReply>-Aktivitäten enthält.  
  
## <a name="see-also"></a>Siehe auch  
 [Vorgehensweise: Erstellen einer Aktivität](https://msdn.microsoft.com/library/c09b1e99-21b5-4d96-9c04-ec31db3f4436)   
 [Erstellen eines Workflowprojekts](../workflow-designer/creating-a-workflow-project.md)