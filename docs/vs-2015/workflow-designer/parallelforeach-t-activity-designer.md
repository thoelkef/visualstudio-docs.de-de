---
title: ParallelForEach&lt;T&gt; Aktivitäts-Designer | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Activities.Statements.ParallelForEach`1.UI
ms.assetid: e93a4843-aef2-4d3e-9a0a-a2d3d1411aa7
caps.latest.revision: 9
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 825906f3de1b2d40d96dc19ed45d2a368d889994
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2019
ms.locfileid: "58962066"
---
# <a name="parallelforeachlttgt-activity-designer"></a>ParallelForEach&lt;T&gt; Aktivitäts-Designer
Die <xref:System.Activities.Statements.ParallelForEach%601>-Aktivität listet die Elemente einer Auflistung auf und führt gleichzeitig, asynchron im gleichen Thread, eine eingebettete Anweisung für jedes Element der Auflistung aus. Verwenden Sie diese Flusssteuerungsaktivität statt der <xref:System.Activities.Statements.Sequence>-Aktivität, wenn von den untergeordneten Aktivitäten dieser Aktivität erwartet werden kann, dass sie in den Leerlauf übergehen.  
  
 Die <xref:System.Activities.Statements.ParallelForEach%601>-Aktivität verfügt über die <xref:System.Activities.Statements.ParallelForEach%601.CompletionCondition%2A>-Eigenschaft, die einen benutzerdefinierten [!INCLUDE[vbprvb](../includes/vbprvb-md.md)]-Ausdruck enthält. Die <xref:System.Activities.Statements.ParallelForEach%601>-Aktivität wertet diese Eigenschaft aus, nachdem alle Branches abgeschlossen sind. Ergibt die Auswertung **"true"**, und klicken Sie dann die <xref:System.Activities.Statements.ParallelForEach%601> -Aktivität abgeschlossen, ohne die anderen Branches auszuführen. Wenn die <xref:System.Activities.Statements.ParallelForEach%601.CompletionCondition%2A> nicht als **"true"**, und klicken Sie dann die <xref:System.Activities.Statements.ParallelForEach%601> Aktivität abgeschlossen wird, wenn alle ihre untergeordneten Aktivitäten abgeschlossen wurden.  
  
## <a name="the-parallelforeacht-activity"></a>Die ParallelForEach\<T >-Aktivität  
 <xref:System.Activities.Statements.ParallelForEach%601> listet seine Werte auf und plant die <xref:System.Activities.Statements.ParallelForEach%601.Body%2A>-Ausführung für jeden aufgelisteten Wert. Es wird nur der <xref:System.Activities.Statements.ParallelForEach%601.Body%2A> geplant. Wie der Textkörper ausgeführt wird, hängt davon ab, ob der <xref:System.Activities.Statements.ParallelForEach%601.Body%2A> in den Leerlauf übergeht.  
  
 Geht der <xref:System.Activities.Statements.ParallelForEach%601.Body%2A> nicht in den Leerlauf über, erfolgt die Ausführung in umgekehrter Reihenfolge, da die geplanten Aktivitäten als Stapel behandelt werden, also die letzte geplante Aktivität als erste ausgeführt wird. Für, wenn Sie z. B. eine Auflistung von {1,2,3,4}in <xref:System.Activities.Statements.ParallelForEach%601> und Verwenden einer **WriteLine** als Textkörper, um den Wert auszugeben. Dann werden die Werte 4, 3, 2, 1 auf der Konsole ausgegeben. Grund hierfür ist, **WriteLine** geht nicht so nach 4 im Leerlauf **WriteLine** Aktivitäten geplant haben, wird sie ausgeführt, mit einem Stapel-Verhalten (first zuletzt).  
  
 Wenn aber Aktivitäten im <xref:System.Activities.Statements.ParallelForEach%601.Body%2A> in den Leerlauf übergehen können, etwa eine <xref:System.ServiceModel.Activities.Receive>-Aktivität oder eine <xref:System.Activities.Statements.Delay>-Aktivität, ergibt sich Folgendes. Dann ist es nicht notwendig, auf den Abschluss zu warten. <xref:System.Activities.Statements.ParallelForEach%601> versucht dann, die nächste geplante Textkörperaktivität auszuführen. Wenn auch diese in den Leerlauf übergeht, bewegt sich <xref:System.Activities.Statements.ParallelForEach%601> zum Textkörper der nächsten Aktivität.  
  
### <a name="using-the-parallelforeacht-activity-designer"></a>Verwenden des ParallelForEach\<T >-Aktivitätsdesigner  
 Die **ParallelForEach\<T >** Aktivitäts-Designer finden Sie in der **Ablaufsteuerung** Kategorie der **Toolbox**, die erfolgt durch Klicken auf die  **Toolbox** auf der linken Seite der Registerkarte die [!INCLUDE[wfd2](../includes/wfd2-md.md)] (Wählen Sie alternativ **Symbolleiste** aus der **Ansicht** Menü oder STRG + ALT + X.)  
  
 Die **ParallelForEach\<T >** Aktivitäts-Designer gezogen werden kann, aus der **Toolbox** und auf die [!INCLUDE[wfd2](../includes/wfd2-md.md)] Oberfläche, wo Aktivitätsdesigner normalerweise platziert werden, für die Beispiel, innerhalb eines eine **Sequenz** Aktivitäts-Designer. Nach dem löschen ihn in das [!INCLUDE[wfd2](../includes/wfd2-md.md)], erstellt eine <xref:System.Activities.Statements.ParallelForEach%601> -Aktivität, die in der Standardeinstellung enthält ein <xref:System.Activities.Activity.DisplayName%2A> von **ParallelForEach\<Int32 >.**  
  
### <a name="parallelforeacht-properties-in-the-workflow-designer"></a>ParallelForEach\<T > Eigenschaften im Workflow-Designer  
 In der folgenden Tabelle werden die nützlichsten Eigenschaften der <xref:System.Activities.Statements.ParallelForEach%601>-Aktivität aufgeführt, und es wird beschrieben, wie sie im Designer verwendet werden.  
  
|Eigenschaftenname|Erforderlich|Verwendung|  
|-------------------|--------------|-----------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|Gibt den benutzerfreundlichen Anzeigenamen des Aktivitätsdesigners im Header an. Der Standardwert ist **ParallelForEach\<Int32 >**. Der Wert kann optional auch bearbeitet werden, der **Eigenschaften** Raster oder direkt im Header Aktivitätsdesigners.|  
|<xref:System.Activities.Statements.ParallelForEach%601.Body%2A>|False|Die Aktivität, die für jedes Element in der Auflistung ausgeführt werden soll. Hinzufügen der <xref:System.Activities.Statements.ParallelForEach%601.Body%2A> -Aktivität, indem Sie eine Aktivität aus der Toolbox in die **Text** Feld der **ParallelForEach\<T >** Aktivitäts-Designer, mit dem Hinweistext "Aktivität hier ablegen".|  
|**TypeArgument**|True|Der Typ der Elemente in der <xref:System.Activities.Statements.ParallelForEach%601.Values%2A> durch den generischen Parameter angegebene Sammlung *T*. In der Standardeinstellung **TypeArgument** nastaven NA hodnotu **Int32**. So ändern Sie den Typ "T" in der **ParallelForEach\<T >** Aktivitäts-Designer, ändern Sie den Wert von der **TypeArgument** Kombinationsfeld im Eigenschaftenraster.|  
|<xref:System.Activities.Statements.ParallelForEach%601.Values%2A>|True|Die Auflistung, deren Elemente durchlaufen werden. Festlegen der <xref:System.Activities.Statements.ParallelForEach%601.Values%2A>, geben Sie einen [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] Ausdruck in der **Werte** Feld der **ForEach\<T >** -Aktivitätsdesigners im Feld mit dem Hinweistext "VB-Ausdruck eingeben" oder auf **Werte** Feld der **Eigenschaften** Fenster.|  
|<xref:System.Activities.Statements.ParallelForEach%601.CompletionCondition%2A>||Die Auswertung erfolgt nach Abschluss der einzelnen Iterationen. Ergibt die Auswertung True, werden die geplanten ausstehenden Iterationen abgebrochen. Wenn diese Eigenschaft nicht festgelegt ist, werden alle geplanten Anweisungen bis zur Beendigung ausgeführt.|  
  
 Standardmäßig hat der Schleifeniterator die Bezeichnung "item". Sie können den Namen der Iteratorvariablen im Ändern der **ForEach** Feld **ParallelForEach\<T >** Aktivitäts-Designer. Der Schleifeniterator kann in den untergeordneten Elementen der <xref:System.Activities.Statements.ParallelForEach%601>-Aktivität in Ausdrücken verwendet werden.  
  
## <a name="see-also"></a>Siehe auch  
 [Sequenz](../workflow-designer/sequence-activity-designer.md)   
 [Parallel](../workflow-designer/parallel-activity-designer.md)   
 [Ablaufsteuerung](../workflow-designer/control-flow-activity-designers.md)