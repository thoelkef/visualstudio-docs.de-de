---
title: Parallele Aktivitäts-Designer | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Parallel.UI
ms.assetid: 0306dc3b-075a-4091-ac3a-96486fbabed5
caps.latest.revision: 10
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 627a99fec632871b815904abd798c0e4bbfd6505
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62971341"
---
# <a name="parallel-activity-designer"></a>Parallel-Aktivitätsdesigner
Die <xref:System.Activities.Statements.Parallel>-Aktivität führt eine Sammlung von untergeordneten Aktivitäten parallel aus.  
  
## <a name="the-parallel-activity"></a>Die Parallel-Aktivität  
 Die <xref:System.Activities.Statements.Parallel>-Aktivität speichert ihre untergeordneten Aktivitäten in einer <xref:System.Activities.Statements.Parallel.Branches%2A>-Auflistung. Verwenden Sie die <xref:System.Activities.Statements.Parallel>-Aktivität statt der <xref:System.Activities.Statements.Sequence>-Aktivität, wenn einige der untergeordneten Aktivitäten sich möglicherweise im Leerlauf befinden könnten.  
  
 Die <xref:System.Activities.Statements.Parallel>-Aktivität verfügt über die <xref:System.Activities.Statements.Parallel.CompletionCondition%2A>-Eigenschaft, die einen benutzerdefinierten [!INCLUDE[vbprvb](../includes/vbprvb-md.md)]-Ausdruck enthält. Die <xref:System.Activities.Statements.Parallel>-Aktivität wertet diese Eigenschaft aus, nachdem alle Branches abgeschlossen sind. Ergibt die Auswertung **"true"**, und klicken Sie dann die <xref:System.Activities.Statements.Parallel> -Aktivität abgeschlossen, ohne die anderen Branches auszuführen. Wenn die <xref:System.Activities.Statements.Parallel.CompletionCondition%2A> nicht als **"true"**, und klicken Sie dann die <xref:System.Activities.Statements.Parallel> Aktivität abgeschlossen wird, wenn alle ihre untergeordneten Aktivitäten abgeschlossen wurden.  
  
### <a name="using-the-parallel-activity-designer"></a>Verwenden des Parallel-Aktivitätsdesigners  
 Die **parallele** Aktivitäts-Designer finden Sie in der **Ablaufsteuerung** Kategorie der **Toolbox**, die erfolgt durch Klicken auf die **Toolbox**auf der linken Seite der Registerkarte die [!INCLUDE[wfd2](../includes/wfd2-md.md)] (Wählen Sie alternativ **Symbolleiste** aus der **Ansicht** Menü oder STRG + ALT + X.)  
  
 Die **parallele** Aktivitäts-Designer gezogen werden kann, aus der **Toolbox** und auf die [!INCLUDE[wfd2](../includes/wfd2-md.md)] -Oberfläche ganz egal, wo Aktivitätsdesigner normalerweise platziert werden, z. B. innerhalb einer **Sequenz** Aktivitäts-Designer. Nach dem löschen ihn in das [!INCLUDE[wfd2](../includes/wfd2-md.md)], erstellt eine <xref:System.Activities.Statements.Parallel> -Aktivität, die in der Standardeinstellung enthält ein <xref:System.Activities.Activity.DisplayName%2A> von **Parallel**  
  
 Eine Aktivität zum Hinzufügen der <xref:System.Activities.Statements.Parallel.Branches%2A> Auflistung von der parallel-Aktivität, ziehen Sie in beliebigen anderen Aktivitätsdesigner aus der **Toolbox** und legen Sie es auf dem Dreieck innerhalb der **parallele** Aktivitäts-Designer. Die Dreiecke flankieren die in den Verzweigungen enthaltenen Aktivitäten. Zusätzliche Aktivitäten können hinzugefügt werden, indem diese Prozedur wiederholt wird. Die Aktivitäten können neu angeordnet werden, per Drag & Drop in die **parallele** Aktivitäts-Designer.  
  
### <a name="parallel-activity-properties-in-the-workflow-designer"></a>Eigenschaften der Parallel-Aktivität im Workflow-Designer  
 In der folgenden Tabelle werden die nützlichsten Eigenschaften der Parallel-Aktivität aufgeführt, und es wird beschrieben, wie sie im Designer verwendet werden.  
  
|Eigenschaftenname|Erforderlich|Verwendung|  
|-------------------|--------------|-----------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|Gibt den benutzerfreundlichen Anzeigenamen des Aktivitätsdesigners im Header an. Der Standardwert ist **parallele**. Der Wert kann optional auch bearbeitet werden, der **Eigenschaften** Raster oder direkt im Header Aktivitätsdesigners.|  
|<xref:System.Activities.Statements.Parallel.Branches%2A>|True|Enthält die Auflistung von untergeordneten Aktivitäten, die ausgeführt werden sollen.|  
|<xref:System.Activities.Statements.Parallel.CompletionCondition%2A>|False|Die Auswertung erfolgt nach Beendigung eines Branches. Ergibt die Auswertung **"true"**, die geplanten ausstehenden Branches abgebrochen. Wenn diese Eigenschaft nicht festgelegt oder ergibt **"false"**, die Aktivität abgeschlossen wird, wenn alle ihre untergeordneten Aktivitäten abgeschlossen wurden. Der Standardwert ist **null**.|  
  
## <a name="see-also"></a>Siehe auch  
 [Sequenz](../workflow-designer/sequence-activity-designer.md)   
 [ParallelForEach\<T>](../workflow-designer/parallelforeach-t-activity-designer.md)   
 [Ablaufsteuerung](../workflow-designer/control-flow-activity-designers.md)