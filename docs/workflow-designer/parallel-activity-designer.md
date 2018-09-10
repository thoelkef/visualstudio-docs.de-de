---
title: Workflow-Designer - Parallel-Aktivitätsdesigner
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
f1_keywords:
- System.Activities.Statements.Parallel.UI
ms.assetid: 0306dc3b-075a-4091-ac3a-96486fbabed5
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 3c4f10b9bb564268f5aeee59d871fd44324097cc
ms.sourcegitcommit: 30f653d9625ba763f6b58f02fb74a24204d064ea
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/25/2018
ms.locfileid: "36756675"
---
# <a name="parallel-activity-designer"></a>Parallel-Aktivitätsdesigner

Die <xref:System.Activities.Statements.Parallel>-Aktivität führt eine Sammlung von untergeordneten Aktivitäten parallel aus.

## <a name="the-parallel-activity"></a>Die Parallel-Aktivität

Die <xref:System.Activities.Statements.Parallel>-Aktivität speichert ihre untergeordneten Aktivitäten in einer <xref:System.Activities.Statements.Parallel.Branches%2A>-Auflistung. Verwenden Sie die <xref:System.Activities.Statements.Parallel>-Aktivität statt der <xref:System.Activities.Statements.Sequence>-Aktivität, wenn einige der untergeordneten Aktivitäten sich möglicherweise im Leerlauf befinden könnten.

Die <xref:System.Activities.Statements.Parallel> Aktivität verfügt über eine <xref:System.Activities.Statements.Parallel.CompletionCondition%2A> -Eigenschaft, die einen Benutzer enthält Visual Basic-Ausdruck angegeben. Die <xref:System.Activities.Statements.Parallel>-Aktivität wertet diese Eigenschaft aus, nachdem alle Verzweigungen abgeschlossen sind. Ergibt die Auswertung **"true"**, und klicken Sie dann die <xref:System.Activities.Statements.Parallel> -Aktivität abgeschlossen, ohne die anderen Branches auszuführen. Wenn die <xref:System.Activities.Statements.Parallel.CompletionCondition%2A> nicht als **"true"**, und klicken Sie dann die <xref:System.Activities.Statements.Parallel> Aktivität abgeschlossen wird, wenn alle ihre untergeordneten Aktivitäten abgeschlossen wurden.

### <a name="using-the-parallel-activity-designer"></a>Verwenden des Parallel-Aktivitätsdesigners

Zugriff die **parallele** Aktivitäts-Designer in der **Ablaufsteuerung** Kategorie der **Toolbox**.

Die **parallele** Aktivitäts-Designer gezogen werden kann, aus der **Toolbox** und sich der Workflow-Designer-Oberfläche gelöscht werden, wo Aktivitätsdesigner normalerweise, z. B. in einer platziertwerden**Sequenz** Aktivitäts-Designer. Nach dem Workflow-Designer ablegen, erstellt er eine <xref:System.Activities.Statements.Parallel> -Aktivität, die in der Standardeinstellung enthält ein <xref:System.Activities.Activity.DisplayName%2A> von **Parallel**

Eine Aktivität zum Hinzufügen der <xref:System.Activities.Statements.Parallel.Branches%2A> Auflistung von der parallel-Aktivität, ziehen Sie in beliebigen anderen Aktivitätsdesigner aus der **Toolbox** und legen Sie es auf dem Dreieck innerhalb der **parallele** Aktivitäts-Designer. Die Dreiecke flankieren die in den Branches enthaltenen Aktivitäten. Zusätzliche Aktivitäten können hinzugefügt werden, indem diese Prozedur wiederholt wird. Die Aktivitäten können neu angeordnet werden, per Drag & Drop in die **parallele** Aktivitäts-Designer.

### <a name="parallel-activity-properties-in-the-workflow-designer"></a>Eigenschaften der Parallel-Aktivität im Workflow-Designer

In der folgenden Tabelle werden die nützlichsten Eigenschaften der Parallel-Aktivität aufgeführt, und es wird beschrieben, wie sie im Designer verwendet werden.

|Eigenschaftenname|Erforderlich|Verwendung|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Gibt den benutzerfreundlichen Anzeigenamen des Aktivitätsdesigners im Header an. Der Standardwert ist **parallele**. Der Wert kann optional auch bearbeitet werden, der **Eigenschaften** Raster oder direkt im Header Aktivitätsdesigners.|
|<xref:System.Activities.Statements.Parallel.Branches%2A>|True|Enthält die Auflistung von untergeordneten Aktivitäten, die ausgeführt werden sollen.|
|<xref:System.Activities.Statements.Parallel.CompletionCondition%2A>|False|Die Auswertung erfolgt nach Beendigung eines Branches. Ergibt die Auswertung **"true"**, die geplanten ausstehenden Branches abgebrochen. Wenn diese Eigenschaft nicht festgelegt oder ergibt **"false"**, die Aktivität abgeschlossen wird, wenn alle ihre untergeordneten Aktivitäten abgeschlossen wurden. Der Standardwert ist **null**.|

## <a name="see-also"></a>Siehe auch

- [Sequenz](../workflow-designer/sequence-activity-designer.md)
- [ParallelForEach\<T>](../workflow-designer/parallelforeach-t-activity-designer.md)
- [Ablaufsteuerung](../workflow-designer/control-flow-activity-designers.md)