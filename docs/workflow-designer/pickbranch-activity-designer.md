---
title: "PickBranch-Aktivitätsdesigner | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: System.Activities.Statements.PickBranch.UI
ms.assetid: f523ad47-bbc0-4cda-a35c-41e67c4ba081
caps.latest.revision: "10"
author: ErikRe
ms.author: erikre
manager: erikre
ms.workload: multiple
ms.openlocfilehash: d583c662de31b990982b78d876bc0046e89089d7
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="pickbranch-activity-designer"></a>PickBranch-Aktivitätsdesigner
Der <xref:System.Activities.Statements.PickBranch> stellt einen ereignisbasierten Ausführungspfad innerhalb einer <xref:System.Activities.Statements.Pick>-Aktivität bereit, der von einem eingehenden Ereignis ausgelöst werden kann.  
  
## <a name="pickbranch"></a>PickBranch  
 <xref:System.Activities.Statements.PickBranch>-Objekte sind in der <xref:System.Activities.Statements.Pick.Branches%2A>-Auflistung einer <xref:System.Activities.Statements.Pick>-Aktivität enthalten. Jede <xref:System.Activities.Statements.PickBranch> ist in einer Verzweigung der <xref:System.Activities.Statements.Pick>-Aktivität enthalten und wird aufgrund eines eingehenden Ereignisses ausgeführt, das als Trigger dient. Auf diese Weise stellt [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)] ereignisbasierte Ablaufsteuerungsmodellierung bereit. Jede <xref:System.Activities.Statements.PickBranch> enthält einen <xref:System.Activities.Statements.PickBranch.Trigger%2A> und eine <xref:System.Activities.Statements.PickBranch.Action%2A>.  
  
### <a name="how-to-use-the-pick-activity-designer"></a>So verwenden Sie den Pick-Aktivitätsdesigner  
 Die **PickBranch** Designer finden Sie in der **Control Flow** Kategorie der **Toolbox**, die erfolgt durch Klicken auf die **Toolbox** Registerkarte [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] (Wählen Sie alternativ **Symbolleiste** aus der **Ansicht** Menüs oder STRG + ALT + X).  
  
 Zwei leere <xref:System.Activities.Statements.PickBranch> Objekte mit den Anzeigenamen von **Branch1** und **branch2 enthält** werden standardmäßig als Elemente des erstellt eine <xref:System.Activities.Statements.Pick> Aktivität bei der **auswählen** Aktivitäts-Designer wird anfänglich abgelegt, auf die [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)]. Die jeweiligen <xref:System.Activities.Statements.PickBranch.DisplayName%2A> Eigenschaftswerte können bearbeitet werden, der **PickBranch** -Designer-Header oder innerhalb der **Eigenschaften** für jede Verzweigung.  
  
 Es gibt zwei Möglichkeiten zum Hinzufügen von <xref:System.Activities.Statements.PickBranch> Objekte auf die Auflistung von einer <xref:System.Activities.Statements.Pick> Objekt: Drag & Drop die **PickBranch** -Designer aus der **Toolbox** oder indem Sie im Kontextmenü den Befehl aus innerhalb der **Pick** Entwurfsoberfläche:  
  
1.  Die **PickBranch** -Designer erstellt eine <xref:System.Activities.Statements.PickBranch> beim aus gezogen der **Toolbox** und in einer der Verzweigungen eines eine **Pick** Aktivitäts-Designer auf die [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] Oberfläche. Die neuen <xref:System.Activities.Statements.PickBranch>-Objekte können im <xref:System.Activities.Statements.Pick>-Designer auf der linken oder rechten Seite jedes <xref:System.Activities.Statements.PickBranch>-Elements platziert werden, das bereits in der Auflistung enthalten ist. Beim Ziehen einer **PickBranch** -Designers auf die **auswählen** Designer mit der Maus, der **auswählen** Designer mithilfe eines vertikalen blaugrauen Bands an, wo die <xref:System.Activities.Statements.PickBranch> wird für entsprechend der gegebenen Mausposition hinzugefügt.  
  
2.  Klicken Sie mit der rechten Maustaste auf **auswählen** Aktivitäts-Designer (jedoch nicht im **PickBranch** Designer) ein Kontextmenü, und wählen Sie **Verzweigung erstellen** zum Hinzufügen einer neuen <xref:System.Activities.Statements.PickBranch>. Beachten Sie, dass die neue <xref:System.Activities.Statements.PickBranch> wird rechts neben den vorhandenen hinzugefügt <xref:System.Activities.Statements.PickBranch> Objekte in der **Pick** Designer.  
  
 Die **PickBranch** Designer kann erweitert werden, damit die **Trigger** und **Aktion** Dialogfelder oder durch Klicken auf die doppelten Caretzeichen auf der rechten Seite ihrer Header reduziert. Bearbeiten der <xref:System.Activities.Statements.PickBranch.Trigger%2A> und <xref:System.Activities.Statements.PickBranch.Action%2A> jedes <xref:System.Activities.Statements.PickBranch> durch Ablegen von Aktivitäten in der **Trigger** und **Aktion** Felder ihrer Designer.  
  
 Die <xref:System.Activities.Statements.PickBranch> Objekte in der <xref:System.Activities.Statements.Pick.Branches%2A> Auflistung von einer <xref:System.Activities.Statements.Pick> Objekt, neu angeordnet werden können, durch Ziehen und Ablegen in eine neue Position innerhalb der **auswählen** Designer. Die **auswählen** Designer mithilfe eines vertikalen blaugrauen Bands an, wo die <xref:System.Activities.Statements.PickBranch> entsprechend der gegebenen Mausposition hinzugefügt wird.  
  
 Es gibt zwei Möglichkeiten, ein <xref:System.Activities.Statements.PickBranch>-Objekt zu löschen:  
  
1.  Wählen Sie die **PickBranch** Designer und löschen Sie ihn.  
  
2.  Wählen Sie die **PickBranch** Designer, mit der rechten Maustaste, erhalten das Kontextmenü und wählen Sie **löschen**.  
  
 Achten Sie darauf, dass Sie wählen die **PickBranch** -Designer-auswählen einer der Aktivitäten in seiner **Trigger** oder **Aktion** Felder versehentlich löscht diese Aktivitäten und nicht die <xref:System.Activities.Statements.PickBranch> Objekt.  
  
### <a name="pickbranch-properties-in-the-workflow-designer"></a>PickBranch-Eigenschaften im Workflow-Designer  
 In der folgenden Tabelle werden die nützlichsten Eigenschaften von <xref:System.Activities.Statements.PickBranch> aufgeführt, und es wird beschrieben, wie sie in [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] verwendet werden.  
  
|Eigenschaftenname|Erforderlich|Verwendung|  
|-------------------|--------------|-----------|  
|<xref:System.Activities.Statements.PickBranch.DisplayName%2A>|False|Im Header des angezeigte benutzerfreundliche Name der **PickBranch** Designer. Der Standardwert lautet Branch.<br /><br /> Obwohl der <xref:System.Activities.Activity.DisplayName%2A> nicht zwingend erforderlich ist, wird empfohlen, einen Anzeigenamen zu verwenden.|  
|<xref:System.Activities.Statements.PickBranch.Trigger%2A>|True|Jedes <xref:System.Activities.Statements.PickBranch>-Objekt enthält eine <xref:System.Activities.Statements.PickBranch.Trigger%2A>-Aktion, die <xref:System.Activities.Statements.PickBranch.Action%2A> aufrufen kann.|  
|<xref:System.Activities.Statements.PickBranch.Action%2A>|False|Jede <xref:System.Activities.Statements.PickBranch>-Objekt enthält eine <xref:System.Activities.Statements.PickBranch.Action%2A>, die ausgeführt wird, sobald sie ausgelöst wird.|  
  
## <a name="see-also"></a>Siehe auch  
 [Ablaufsteuerung](../workflow-designer/control-flow-activity-designers.md)   
 [Auswahlaktivität](/dotnet/framework/windows-workflow-foundation/pick-activity)   
 [Verwenden der Pick-Aktivität](/dotnet/framework/windows-workflow-foundation/samples/using-the-pick-activity)