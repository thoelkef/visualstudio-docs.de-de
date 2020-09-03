---
title: Workflow-Designer paralleler Aktivitäts Designer
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Parallel.UI
ms.assetid: 0306dc3b-075a-4091-ac3a-96486fbabed5
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3f07dd02f682cd5c61d4d17099c1aeb76bb39bf8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "75593160"
---
# <a name="parallel-activity-designer"></a>Parallel-Aktivitätsdesigner

Die <xref:System.Activities.Statements.Parallel>-Aktivität führt eine Sammlung von untergeordneten Aktivitäten parallel aus.

## <a name="the-parallel-activity"></a>Die Parallel-Aktivität

Die <xref:System.Activities.Statements.Parallel>-Aktivität speichert ihre untergeordneten Aktivitäten in einer <xref:System.Activities.Statements.Parallel.Branches%2A>-Auflistung. Verwenden Sie die <xref:System.Activities.Statements.Parallel>-Aktivität statt der <xref:System.Activities.Statements.Sequence>-Aktivität, wenn einige der untergeordneten Aktivitäten sich möglicherweise im Leerlauf befinden könnten.

Die- <xref:System.Activities.Statements.Parallel> Aktivität verfügt über eine- <xref:System.Activities.Statements.Parallel.CompletionCondition%2A> Eigenschaft, die einen vom Benutzer angegebenen Visual Basic Ausdruck enthält. Die <xref:System.Activities.Statements.Parallel>-Aktivität wertet diese Eigenschaft aus, nachdem alle Branches abgeschlossen sind. Wenn **true**ausgewertet wird, wird die- <xref:System.Activities.Statements.Parallel> Aktivität abgeschlossen, ohne dass die anderen Verzweigungen ausgeführt werden. Wenn das-Element <xref:System.Activities.Statements.Parallel.CompletionCondition%2A> nicht als **true**ausgewertet wird, wird die-Aktivität abgeschlossen, <xref:System.Activities.Statements.Parallel> Wenn alle untergeordneten Aktivitäten abgeschlossen sind.

### <a name="using-the-parallel-activity-designer"></a>Verwenden des Parallel-Aktivitätsdesigners

Greifen Sie in der Kategorie **Ablauf Steuerung** der **Toolbox**auf den **parallel** -Aktivitäts Designer zu.

Der **parallel** -Aktivitäts Designer kann aus der **Toolbox** gezogen und auf der Workflow-Designer-Oberfläche dort abgelegt werden, wo Aktivitäts Designer normalerweise platziert werden, z. b. innerhalb eines **Sequence** -Aktivitäts Designers. Nachdem Sie Sie in der Workflow-Designer abgelegt haben, wird eine- <xref:System.Activities.Statements.Parallel> Aktivität erstellt, die standardmäßig eine <xref:System.Activities.Activity.DisplayName%2A> von **parallel** enthält.

Wenn Sie der-Auflistung der parallelen Aktivität eine Aktivität hinzufügen möchten <xref:System.Activities.Statements.Parallel.Branches%2A> , ziehen Sie einen anderen Aktivitäts Designer aus der **Toolbox** , und legen Sie ihn auf dem Dreieck innerhalb des **parallel** -Aktivitäts Designers ab. Die Dreiecke flankieren die in den Verzweigungen enthaltenen Aktivitäten. Zusätzliche Aktivitäten können hinzugefügt werden, indem diese Prozedur wiederholt wird. Die Aktivitäten können durchziehen und ablegen innerhalb des **parallel** -Aktivitäts Designers neu angeordnet werden.

### <a name="parallel-activity-properties-in-the-workflow-designer"></a>Eigenschaften der Parallel-Aktivität im Workflow-Designer

In der folgenden Tabelle werden die nützlichsten Eigenschaften der Parallel-Aktivität aufgeführt, und es wird beschrieben, wie sie im Designer verwendet werden.

|Eigenschaftenname|Erforderlich|Verbrauch|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|Falsch|Gibt den benutzerfreundlichen Anzeigenamen des Aktivitätsdesigners im Header an. Der Standardwert ist **parallel**. Der Wert kann optional im **Eigenschaften** Raster oder direkt im Header des Aktivitäts Designers bearbeitet werden.|
|<xref:System.Activities.Statements.Parallel.Branches%2A>|Richtig|Enthält die Auflistung von untergeordneten Aktivitäten, die ausgeführt werden sollen.|
|<xref:System.Activities.Statements.Parallel.CompletionCondition%2A>|Falsch|Die Auswertung erfolgt nach Beendigung eines Branches. Wenn **true**ausgewertet wird, werden die geplanten ausstehenden branches abgebrochen. Wenn diese Eigenschaft nicht festgelegt oder als **false**ausgewertet wird, wird die-Aktivität abgeschlossen, wenn alle untergeordneten Aktivitäten abgeschlossen sind. Der Standardwert lautet **null**.|

## <a name="see-also"></a>Weitere Informationen

- [Sequenz](../workflow-designer/sequence-activity-designer.md)
- [ParallelForEach\<T>](../workflow-designer/parallelforeach-t-activity-designer.md)
- [Ablaufsteuerung](../workflow-designer/control-flow-activity-designers.md)
