---
title: Parallele Aktivitäts-Designer | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Parallel.UI
ms.assetid: 0306dc3b-075a-4091-ac3a-96486fbabed5
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: b1c3f24af736dfd3762de7942ba1f52442dfd20c
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="parallel-activity-designer"></a>Parallel-Aktivitätsdesigner
Die <xref:System.Activities.Statements.Parallel>-Aktivität führt eine Sammlung von untergeordneten Aktivitäten parallel aus.

## <a name="the-parallel-activity"></a>Die Parallel-Aktivität
 Die <xref:System.Activities.Statements.Parallel>-Aktivität speichert ihre untergeordneten Aktivitäten in einer <xref:System.Activities.Statements.Parallel.Branches%2A>-Auflistung. Verwenden Sie die <xref:System.Activities.Statements.Parallel>-Aktivität statt der <xref:System.Activities.Statements.Sequence>-Aktivität, wenn einige der untergeordneten Aktivitäten sich möglicherweise im Leerlauf befinden könnten.

 Die <xref:System.Activities.Statements.Parallel>-Aktivität verfügt über die <xref:System.Activities.Statements.Parallel.CompletionCondition%2A>-Eigenschaft, die einen benutzerdefinierten [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]-Ausdruck enthält. Die <xref:System.Activities.Statements.Parallel>-Aktivität wertet diese Eigenschaft aus, nachdem alle Verzweigungen abgeschlossen sind. Ergibt die Auswertung **"true"**, und klicken Sie dann die <xref:System.Activities.Statements.Parallel> -Aktivität abgeschlossen, ohne die anderen Verzweigungen auszuführen. Wenn die <xref:System.Activities.Statements.Parallel.CompletionCondition%2A> wird nicht ausgewertet **"true"**, und klicken Sie dann die <xref:System.Activities.Statements.Parallel> Aktivität abgeschlossen wird, wenn alle untergeordneten Aktivitäten abgeschlossen sind.

### <a name="using-the-parallel-activity-designer"></a>Verwenden des Parallel-Aktivitätsdesigners
 Die **Parallel** Aktivitäts-Designer finden Sie in der **Control Flow** Kategorie der **Toolbox**, die erfolgt durch Klicken auf die **Toolbox**auf der linken Seite der Registerkarte die [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] (Wählen Sie alternativ **Symbolleiste** aus der **Ansicht** Menüs oder STRG + ALT + X drücken.)

 Die **parallele** Aktivitäts-Designer gezogen werden kann, aus der **Toolbox** gezogen und auf die [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] -Oberfläche ablegen, wo Aktivitätsdesigner normalerweise platziert werden, z. B. innerhalb einer **Sequenz** Aktivitäts-Designer. Nach dem löschen ihn in die [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)], erstellt eine <xref:System.Activities.Statements.Parallel> -Aktivität, die in der Standardeinstellung enthält eine <xref:System.Activities.Activity.DisplayName%2A> von **Parallel**

 Eine Aktivität zum Hinzufügen der <xref:System.Activities.Statements.Parallel.Branches%2A> -Auflistung der parallelen Aktivität ziehen beliebigen anderen Aktivitätsdesigner aus der **Toolbox** und legen Sie es auf dem Dreieck innerhalb der **parallele** Aktivitäts-Designer. Die Dreiecke flankieren die in den Branches enthaltenen Aktivitäten. Zusätzliche Aktivitäten können hinzugefügt werden, indem diese Prozedur wiederholt wird. Die Aktivitäten können neu angeordnet werden, per Drag & Drop innerhalb der **parallele** Aktivitäts-Designer.

### <a name="parallel-activity-properties-in-the-workflow-designer"></a>Eigenschaften der Parallel-Aktivität im Workflow-Designer
 In der folgenden Tabelle werden die nützlichsten Eigenschaften der Parallel-Aktivität aufgeführt, und es wird beschrieben, wie sie im Designer verwendet werden.

|Eigenschaftenname|Erforderlich|Verwendung|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Gibt den benutzerfreundlichen Anzeigenamen des Aktivitätsdesigners im Header an. Der Standardwert ist **parallele**. Der Wert kann optional bearbeitet werden, der **Eigenschaften** Raster oder direkt im Header Aktivitätsdesigners.|
|<xref:System.Activities.Statements.Parallel.Branches%2A>|True|Enthält die Auflistung von untergeordneten Aktivitäten, die ausgeführt werden sollen.|
|<xref:System.Activities.Statements.Parallel.CompletionCondition%2A>|False|Die Auswertung erfolgt nach Beendigung eines Branches. Ergibt die Auswertung **"true"**, die geplanten ausstehenden Verzweigungen abgebrochen. Wenn diese Eigenschaft nicht festgelegt oder ergibt **"false"**, die Aktivität abgeschlossen wird, wenn alle untergeordneten Aktivitäten abgeschlossen sind. Der Standardwert ist **null**.|

## <a name="see-also"></a>Siehe auch

- [Sequenz](../workflow-designer/sequence-activity-designer.md)
- [ParallelForEach\<T>](../workflow-designer/parallelforeach-t-activity-designer.md)
- [Ablaufsteuerung](../workflow-designer/control-flow-activity-designers.md)