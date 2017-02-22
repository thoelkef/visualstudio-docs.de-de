---
title: "ParallelForEach&lt;T&gt;-Aktivit&#228;tsdesigner | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "System.Activities.Statements.ParallelForEach`1.UI"
ms.assetid: e93a4843-aef2-4d3e-9a0a-a2d3d1411aa7
caps.latest.revision: 9
caps.handback.revision: 9
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
---
# ParallelForEach&lt;T&gt;-Aktivit&#228;tsdesigner
Die <xref:System.Activities.Statements.ParallelForEach%601>\-Aktivität listet die Elemente einer Auflistung auf und führt gleichzeitig, asynchron im gleichen Thread, eine eingebettete Anweisung für jedes Element der Auflistung aus.Verwenden Sie diese Flusssteuerungsaktivität statt der <xref:System.Activities.Statements.Sequence>\-Aktivität, wenn von den untergeordneten Aktivitäten dieser Aktivität erwartet werden kann, dass sie in den Leerlauf übergehen.  
  
 Die <xref:System.Activities.Statements.ParallelForEach%601>\-Aktivität verfügt über die <xref:System.Activities.Statements.ParallelForEach%601.CompletionCondition%2A>\-Eigenschaft, die einen benutzerdefinierten [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]\-Ausdruck enthält.Die <xref:System.Activities.Statements.ParallelForEach%601>\-Aktivität wertet diese Eigenschaft aus, nachdem alle Verzweigungen abgeschlossen sind.Wenn die Eigenschaft **true** ergibt, dann wird die <xref:System.Activities.Statements.ParallelForEach%601>\-Aktivität abgeschlossen, ohne die anderen Verzweigungen auszuführen.Wenn <xref:System.Activities.Statements.ParallelForEach%601.CompletionCondition%2A> nicht den Wert **true** ergibt, dann wird die <xref:System.Activities.Statements.ParallelForEach%601>\-Aktivität abgeschlossen, sobald alle seine untergeordneten Aktivitäten abgeschlossen sind.  
  
## Die ParallelForEach\<T\>\-Aktivität  
 <xref:System.Activities.Statements.ParallelForEach%601> listet seine Werte auf und plant die <xref:System.Activities.Statements.ParallelForEach%601.Body%2A>\-Ausführung für jeden aufgelisteten Wert.Es wird nur der <xref:System.Activities.Statements.ParallelForEach%601.Body%2A> geplant.Wie der Textkörper ausgeführt wird, hängt davon ab, ob der <xref:System.Activities.Statements.ParallelForEach%601.Body%2A> in den Leerlauf übergeht.  
  
 Geht der <xref:System.Activities.Statements.ParallelForEach%601.Body%2A> nicht in den Leerlauf über, erfolgt die Ausführung in umgekehrter Reihenfolge, da die geplanten Aktivitäten als Stapel behandelt werden, also die letzte geplante Aktivität als erste ausgeführt wird.Angenommen, eine Auflistung enthält {1,2,3,4} in <xref:System.Activities.Statements.ParallelForEach%601> und verwendet **WriteLine** als Textkörper, um den jeweiligen Wert auszugeben.Dann werden die Werte 4, 3, 2, 1 auf der Konsole ausgegeben.Dies deshalb, weil **WriteLine** nicht in den Leerlauf übergeht, weshalb 4 **WriteLine**\-Aktivitäten geplant wurden, die dem Stapelverhalten entsprechend \(die zuletzt geplante Aktivität wird als erste ausgeführt\) ausgeführt werden.  
  
 Wenn aber Aktivitäten im <xref:System.Activities.Statements.ParallelForEach%601.Body%2A> in den Leerlauf übergehen können, etwa eine <xref:System.ServiceModel.Activities.Receive>\-Aktivität oder eine <xref:System.Activities.Statements.Delay>\-Aktivität, ergibt sich Folgendes.Dann gibt es keine Notwendigkeit, mit der Ausführung zu warten.<xref:System.Activities.Statements.ParallelForEach%601> versucht dann, die nächste geplante Textkörperaktivität auszuführen.Wenn auch diese in den Leerlauf übergeht, bewegt sich <xref:System.Activities.Statements.ParallelForEach%601> zum Textkörper der nächsten Aktivität.  
  
### Verwenden des ParallelForEach\<T\>\-Aktivitätsdesigners  
 Der **ParallelForEach\<T\>**\-Aktivitätsdesigner befindet sich in der Kategorie **Ablaufsteuerung** der **Toolbox**, auf die Sie zugreifen können, indem Sie auf der linken Seite von [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] auf die Registerkarte **Toolbox** klicken \(Sie können auch im Menü **Ansicht** den Befehl **Symbolleiste** auswählen oder STRG\+ALT\+X drücken\).  
  
 Der **ParallelForEach\<T\>**\-Aktivitätsdesigner kann aus der **Toolbox** gezogen und auf der [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)]\-Oberfläche dort abgelegt werden, wo Aktivitätsdesigner normalerweise platziert werden, z. B. innerhalb eines **Sequence**\-Aktivitätsdesigners.Nachdem der Aktivitätsdesigner in [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] abgelegt wurde, erstellt er eine <xref:System.Activities.Statements.ParallelForEach%601>\-Aktivität mit dem standardmäßigen <xref:System.Activities.Activity.DisplayName%2A>**ParallelForEach\<Int32\>.**  
  
### ParallelForEach\-\<T\>\-Eigenschaften im Workflow\-Designer  
 In der folgenden Tabelle werden die nützlichsten Eigenschaften der <xref:System.Activities.Statements.ParallelForEach%601>\-Aktivität aufgeführt, und es wird beschrieben, wie sie im Designer verwendet werden.  
  
|Eigenschaftenname|Erforderlich|Verwendung|  
|-----------------------|------------------|----------------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|Gibt den benutzerfreundlichen Anzeigenamen des Aktivitätsdesigners im Header an.Der Standardwert lautet **ParallelForEach\<Int32\>**.Der Wert kann optional im Raster **Eigenschaften** oder direkt im Header des Aktivitätsdesigners bearbeitet werden.|  
|<xref:System.Activities.Statements.ParallelForEach%601.Body%2A>|False|Die Aktivität, die für jedes Element in der Auflistung ausgeführt werden soll.Sie fügen die <xref:System.Activities.Statements.ParallelForEach%601.Body%2A>\-Aktivität hinzu, indem Sie eine Aktivität aus der Toolbox in das Feld **Body** mit dem Hinweistext "Aktivität hier ablegen" des **ParallelForEach\<T\>**\-Aktivitätsdesigners ziehen.|  
|**TypeArgument**|True|Der Typ der Elemente in der <xref:System.Activities.Statements.ParallelForEach%601.Values%2A>\-Auflistung, der durch den generischen Parameter *T* angegeben wird.Standardmäßig ist **TypeArgument** auf **Int32** festgelegt.Um den Typ T im **ParallelForEach\<T\>**\-Aktivitätsdesigner zu ändern, wählen Sie im Eigenschaftenraster für **TypeArgument** im Kombinationsfeld einen anderen Wert aus.|  
|<xref:System.Activities.Statements.ParallelForEach%601.Values%2A>|True|Die Auflistung, deren Elemente durchlaufen werden.Um <xref:System.Activities.Statements.ParallelForEach%601.Values%2A> festzulegen, geben Sie im Feld **Werte** des **ForEach\<T\>**\-Aktivitätsdesigner im Feld mit dem Hinweistext "VB\-Ausdruck eingeben" oder im Feld **Werte** des Fensters **Eigenschaften** einen [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]\-Ausdruck ein.|  
|<xref:System.Activities.Statements.ParallelForEach%601.CompletionCondition%2A>||Die Auswertung erfolgt nach Abschluss der einzelnen Iterationen.Ergibt die Auswertung True, werden die geplanten ausstehenden Iterationen abgebrochen.Wenn diese Eigenschaft nicht festgelegt ist, werden alle geplanten Anweisungen bis zur Beendigung ausgeführt.|  
  
 Standardmäßig hat der Schleifeniterator die Bezeichnung "item".Sie können den Namen der Iteratorvariablen im Feld **ForEach** des **ParallelForEach\<T\>**\-Aktivitätsdesigners ändern.Der Schleifeniterator kann in den untergeordneten Elementen der <xref:System.Activities.Statements.ParallelForEach%601>\-Aktivität in Ausdrücken verwendet werden.  
  
## Siehe auch  
 [Sequence](../workflow-designer/sequence-activity-designer.md)   
 [Parallel](../workflow-designer/parallel-activity-designer.md)   
 [Ablaufsteuerung](../workflow-designer/control-flow-activity-designers.md)