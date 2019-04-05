---
title: PickBranch-Aktivitätsdesigner | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Activities.Statements.PickBranch.UI
ms.assetid: f523ad47-bbc0-4cda-a35c-41e67c4ba081
caps.latest.revision: 10
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: d83b4945b41c26ace1b36a294f1830fdbb24d319
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2019
ms.locfileid: "58961350"
---
# <a name="pickbranch-activity-designer"></a>PickBranch-Aktivitätsdesigner
Der <xref:System.Activities.Statements.PickBranch> stellt einen ereignisbasierten Ausführungspfad innerhalb einer <xref:System.Activities.Statements.Pick>-Aktivität bereit, der von einem eingehenden Ereignis ausgelöst werden kann.  
  
## <a name="pickbranch"></a>PickBranch  
 <xref:System.Activities.Statements.PickBranch>-Objekte sind in der <xref:System.Activities.Statements.Pick.Branches%2A>-Auflistung einer <xref:System.Activities.Statements.Pick>-Aktivität enthalten. Jede <xref:System.Activities.Statements.PickBranch> ist in einem Branch der <xref:System.Activities.Statements.Pick>-Aktivität enthalten und wird aufgrund eines eingehenden Ereignisses ausgeführt, das als Trigger dient. Auf diese Weise stellt [!INCLUDE[wfd1](../includes/wfd1-md.md)] ereignisbasierte Ablaufsteuerungsmodellierung bereit. Jede <xref:System.Activities.Statements.PickBranch> enthält einen <xref:System.Activities.Statements.PickBranch.Trigger%2A> und eine <xref:System.Activities.Statements.PickBranch.Action%2A>.  
  
### <a name="how-to-use-the-pick-activity-designer"></a>So verwenden Sie den Pick-Aktivitätsdesigner  
 Die **PickBranch** Designer finden Sie in der **Ablaufsteuerung** Kategorie der **Toolbox**, die erfolgt durch Klicken auf die **Toolbox** Registerkarte [!INCLUDE[wfd2](../includes/wfd2-md.md)] (Wählen Sie alternativ **Symbolleiste** aus der **Ansicht** Menü oder STRG + ALT + X).  
  
 Zwei leere <xref:System.Activities.Statements.PickBranch> Objekte mit den Anzeigenamen **Branch1** und **Branch2** werden als Elemente standardmäßig erstellt eine <xref:System.Activities.Statements.Pick> Aktivität bei der **auswählen** Aktivitäts-Designer wird anfänglich gelöscht, auf die [!INCLUDE[wfd2](../includes/wfd2-md.md)]. Die jeweiligen <xref:System.Activities.Statements.PickBranch.DisplayName%2A> Eigenschaftswerte können bearbeitet werden, der **PickBranch** Designer-Header oder in der **Eigenschaften** für jeden Branch.  
  
 Es gibt zwei Möglichkeiten zum Hinzufügen von <xref:System.Activities.Statements.PickBranch> Objekte auf die Auflistung von einer <xref:System.Activities.Statements.Pick> Objekt: Ziehen und Ablegen der **PickBranch** -Designer aus der **Toolbox** oder über das Kontextmenü in in der **auswählen** Entwurfsoberfläche:  
  
1. Die **PickBranch** -Designer erstellt eine <xref:System.Activities.Statements.PickBranch> Wenn es gezogen wird von der **Toolbox** und in einer der Verzweigungen einer **auswählen** Aktivitäts-Designer auf die [!INCLUDE[wfd2](../includes/wfd2-md.md)] Oberfläche. Die neuen <xref:System.Activities.Statements.PickBranch>-Objekte können im <xref:System.Activities.Statements.Pick>-Designer auf der linken oder rechten Seite jedes <xref:System.Activities.Statements.PickBranch>-Elements platziert werden, das bereits in der Auflistung enthalten ist. Beim Ziehen einer **PickBranch** Designer auf die **auswählen** mit der Maus, die **auswählen** Designer mithilfe ein vertikales blaugrauen Bands an, wo entsprechend der <xref:System.Activities.Statements.PickBranch> wird für den gegebenen Mausposition hinzugefügt.  
  
2. Klicken Sie mit der rechten Maustaste auf **auswählen** -Aktivitätsdesigner (jedoch nicht im **PickBranch** Designer) ein Kontextmenü und wählen Sie **Verzweigung erstellen** zum Hinzufügen einer neuen <xref:System.Activities.Statements.PickBranch>. Beachten Sie, dass die neue <xref:System.Activities.Statements.PickBranch> wird hinzugefügt, die rechts neben den vorhandenen <xref:System.Activities.Statements.PickBranch> Objekte in der **auswählen** Designer.  
  
   Die **PickBranch** Designer kann erweitert werden, damit die **Trigger** und **Aktion** Dialogfelder oder durch Klicken auf die doppelten Caretzeichen auf der rechten Seite ihrer Header reduziert. Bearbeiten der <xref:System.Activities.Statements.PickBranch.Trigger%2A> und <xref:System.Activities.Statements.PickBranch.Action%2A> aller <xref:System.Activities.Statements.PickBranch> durch Ablegen von Aktivitäten in der **Trigger** und **Aktion** Felder ihrer Designer.  
  
   Der <xref:System.Activities.Statements.PickBranch> Objekte in der <xref:System.Activities.Statements.Pick.Branches%2A> Auflistung von einer <xref:System.Activities.Statements.Pick> Objekt, das neu angeordnet werden können, durch Ziehen und Ablegen in einem neuen Speicherort innerhalb der **auswählen** Designer. Die **auswählen** Designer mithilfe ein vertikales blaugrauen Bands an, wo entsprechend der <xref:System.Activities.Statements.PickBranch> gegebenen Mausposition hinzugefügt wird.  
  
   Es gibt zwei Möglichkeiten, ein <xref:System.Activities.Statements.PickBranch>-Objekt zu löschen:  
  
3. Wählen Sie die **PickBranch** Designer und löschen Sie sie.  
  
4. Wählen Sie die **PickBranch** Designer, mit der rechten Maustaste das Kontextmenü, und wählen Sie **löschen**.  
  
   Wählen Sie die **PickBranch** Designer, wie die Auswahl einer der Aktivitäten in dessen **Trigger** oder **Aktion** Felder versehentlich löscht diese Aktivitäten und nicht die <xref:System.Activities.Statements.PickBranch> Objekt.  
  
### <a name="pickbranch-properties-in-the-workflow-designer"></a>PickBranch-Eigenschaften im Workflow-Designer  
 In der folgenden Tabelle werden die nützlichsten Eigenschaften von <xref:System.Activities.Statements.PickBranch> aufgeführt, und es wird beschrieben, wie sie in [!INCLUDE[wfd2](../includes/wfd2-md.md)] verwendet werden.  
  
|Eigenschaftenname|Erforderlich|Verwendung|  
|-------------------|--------------|-----------|  
|<xref:System.Activities.Statements.PickBranch.DisplayName%2A>|False|Der Anzeigename für den Header von den **PickBranch** Designer. Der Standardwert lautet Branch.<br /><br /> Obwohl der <xref:System.Activities.Activity.DisplayName%2A> nicht zwingend erforderlich ist, wird empfohlen, einen Anzeigenamen zu verwenden.|  
|<xref:System.Activities.Statements.PickBranch.Trigger%2A>|True|Jedes <xref:System.Activities.Statements.PickBranch>-Objekt enthält eine <xref:System.Activities.Statements.PickBranch.Trigger%2A>-Aktion, die <xref:System.Activities.Statements.PickBranch.Action%2A> aufrufen kann.|  
|<xref:System.Activities.Statements.PickBranch.Action%2A>|False|Jede <xref:System.Activities.Statements.PickBranch>-Objekt enthält eine <xref:System.Activities.Statements.PickBranch.Action%2A>, die ausgeführt wird, sobald sie ausgelöst wird.|  
  
## <a name="see-also"></a>Siehe auch  
 [Ablaufsteuerung](../workflow-designer/control-flow-activity-designers.md)   
 [Auswählen der Aktivität](http://msdn.microsoft.com/library/b3e49b7f-0285-4720-8c09-11ae18f0d53e)   
 [Verwenden der Pick-Aktivität](http://msdn.microsoft.com/library/b89be812-a247-4025-b0e3-ffb20db027a6)