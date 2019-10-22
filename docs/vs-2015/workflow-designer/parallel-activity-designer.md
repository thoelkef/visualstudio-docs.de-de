---
title: Paralleler Aktivitäts Designer | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Parallel.UI
ms.assetid: 0306dc3b-075a-4091-ac3a-96486fbabed5
caps.latest.revision: 10
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: a46a340ccdeacacb8f04b962313db18975447a67
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2019
ms.locfileid: "72672637"
---
# <a name="parallel-activity-designer"></a>Parallel-Aktivitätsdesigner
Die <xref:System.Activities.Statements.Parallel>-Aktivität führt eine Sammlung von untergeordneten Aktivitäten parallel aus.

## <a name="the-parallel-activity"></a>Die Parallel-Aktivität
 Die <xref:System.Activities.Statements.Parallel>-Aktivität speichert ihre untergeordneten Aktivitäten in einer <xref:System.Activities.Statements.Parallel.Branches%2A>-Auflistung. Verwenden Sie die <xref:System.Activities.Statements.Parallel>-Aktivität statt der <xref:System.Activities.Statements.Sequence>-Aktivität, wenn einige der untergeordneten Aktivitäten sich möglicherweise im Leerlauf befinden könnten.

 Die <xref:System.Activities.Statements.Parallel>-Aktivität verfügt über die <xref:System.Activities.Statements.Parallel.CompletionCondition%2A>-Eigenschaft, die einen benutzerdefinierten [!INCLUDE[vbprvb](../includes/vbprvb-md.md)]-Ausdruck enthält. Die <xref:System.Activities.Statements.Parallel>-Aktivität wertet diese Eigenschaft aus, nachdem alle Branches abgeschlossen sind. Wenn **true**ausgewertet wird, wird die <xref:System.Activities.Statements.Parallel> Aktivität abgeschlossen, ohne dass die anderen Verzweigungen ausgeführt werden. Wenn die <xref:System.Activities.Statements.Parallel.CompletionCondition%2A> nicht als **true**ausgewertet wird, wird die <xref:System.Activities.Statements.Parallel> Aktivität abgeschlossen, wenn alle untergeordneten Aktivitäten abgeschlossen sind.

### <a name="using-the-parallel-activity-designer"></a>Verwenden des Parallel-Aktivitätsdesigners
 Der **parallele** Aktivitäts Designer befindet sich in der Kategorie **Ablauf Steuerung** der **Toolbox**, auf **die Sie zugreifen** können, indem Sie auf der linken Seite der [!INCLUDE[wfd2](../includes/wfd2-md.md)] auf die Registerkarte **Toolbox** klicken (Sie **können auch im Feld Menü anzeigen** oder STRG + ALT + X.)

 Der **parallel** -Aktivitäts Designer kann aus der **Toolbox** gezogen und auf der [!INCLUDE[wfd2](../includes/wfd2-md.md)]-Oberfläche dort abgelegt werden, wo Aktivitäts Designer normalerweise platziert werden, z. b. innerhalb eines **Sequence** -Aktivitäts Designers. Nach dem ablegen im [!INCLUDE[wfd2](../includes/wfd2-md.md)] wird eine <xref:System.Activities.Statements.Parallel>-Aktivität erstellt, die standardmäßig eine <xref:System.Activities.Activity.DisplayName%2A> **parallel** enthält.

 Um der <xref:System.Activities.Statements.Parallel.Branches%2A>-Auflistung der Parallel-Aktivität eine Aktivität hinzuzufügen, ziehen Sie einen anderen Aktivitäts Designer aus der **Toolbox** , und legen Sie ihn auf dem Dreieck innerhalb des **parallel** -Aktivitäts Designers ab. Die Dreiecke flankieren die in den Verzweigungen enthaltenen Aktivitäten. Zusätzliche Aktivitäten können hinzugefügt werden, indem diese Prozedur wiederholt wird. Die Aktivitäten können durchziehen und ablegen innerhalb des **parallel** -Aktivitäts Designers neu angeordnet werden.

### <a name="parallel-activity-properties-in-the-workflow-designer"></a>Eigenschaften der Parallel-Aktivität im Workflow-Designer
 In der folgenden Tabelle werden die nützlichsten Eigenschaften der Parallel-Aktivität aufgeführt, und es wird beschrieben, wie sie im Designer verwendet werden.

|Eigenschaftenname|Erforderlich|Verwendung|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Gibt den benutzerfreundlichen Anzeigenamen des Aktivitätsdesigners im Header an. Der Standardwert ist **parallel**. Der Wert kann optional im **Eigenschaften** Raster oder direkt im Header des Aktivitäts Designers bearbeitet werden.|
|<xref:System.Activities.Statements.Parallel.Branches%2A>|True|Enthält die Auflistung von untergeordneten Aktivitäten, die ausgeführt werden sollen.|
|<xref:System.Activities.Statements.Parallel.CompletionCondition%2A>|False|Die Auswertung erfolgt nach Beendigung eines Branches. Wenn **true**ausgewertet wird, werden die geplanten ausstehenden branches abgebrochen. Wenn diese Eigenschaft nicht festgelegt oder als **false**ausgewertet wird, wird die-Aktivität abgeschlossen, wenn alle untergeordneten Aktivitäten abgeschlossen sind. Der Standardwert ist **null**.|

## <a name="see-also"></a>Siehe auch
 [Sequenz](../workflow-designer/sequence-activity-designer.md) [ParallelForEach \<T >](../workflow-designer/parallelforeach-t-activity-designer.md) Ablauf [Steuerung](../workflow-designer/control-flow-activity-designers.md)