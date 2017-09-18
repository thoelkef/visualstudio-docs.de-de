---
title: "InvokeMethod-Aktivit&#228;tsdesigner | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "System.Activities.Statements.InvokeMethod.UI"
ms.assetid: 15e6efdc-52ca-46d8-9c5e-063f7c8265a6
caps.latest.revision: 6
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 6
---
# InvokeMethod-Aktivit&#228;tsdesigner
**InvokeMethod**\-Designer wird verwendet, um eine <xref:System.Activities.Statements.InvokeMethod>\-Aktivität zu erstellen und zu konfigurieren.  
  
## Die InvokeMethod\-Aktivität  
 Die <xref:System.Activities.Statements.InvokeMethod>\-Aktivität ruft eine öffentliche Methode eines angegebenen Objekts oder Typs auf.  
  
### Verwenden des InvokeMethod\-Aktivitätsdesigners  
 Der **InvokeMethod**\-Aktivitätsdesigner befindet sich in der Kategorie **Primitives** der **Toolbox**, auf die Sie zugreifen können, indem Sie in [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] auf die Registerkarte **Toolbox** klicken \(Sie können auch im Menü **Ansicht** den Befehl **Toolbox** auswählen oder STRG\+ALT\+X drücken\).  
  
 Der **InvokeMethod**\-Aktivitätsdesigner kann aus der **Toolbox** gezogen und auf der [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)]\-Oberfläche dort abgelegt werden, wo Aktivitäten normalerweise platziert werden, etwa innerhalb einer <xref:System.Activities.Statements.Sequence>.Daraufhin wird eine <xref:System.Activities.Statements.InvokeMethod>\-Aktivität mit dem <xref:System.Activities.Activity.DisplayName%2A>\-Standardwert InvokeMethod erstellt.Der <xref:System.Activities.Activity.DisplayName%2A>\-Wert kann im Header des **InvokeMethod**\-Aktivitätsdesigners oder im Feld **DisplayName** des Eigenschaftenrasters bearbeitet werden.  
  
### Die InvokeMethod\-Eigenschaften  
 In der folgenden Tabelle werden die <xref:System.Activities.Statements.InvokeMethod>\-Eigenschaften aufgeführt, und es wird beschrieben, wie sie im Designer verwendet werden.Diese Eigenschaften können im Eigenschaftenraster bearbeitet werden, einige davon können auch in der [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)]\-Designeroberfläche bearbeitet werden.  
  
|Eigenschaftenname|Erforderlich|Verwendung|  
|-----------------------|------------------|----------------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|Gibt den Anzeigenamen der <xref:System.Activities.Statements.InvokeMethod>\-Aktivität an.Der Standardwert lautet InvokeMethod.<br /><br /> Obwohl der <xref:System.Activities.Activity.DisplayName%2A> nicht zwingend erforderlich ist, wird empfohlen, einen Anzeigenamen zu verwenden.|  
|<xref:System.Activities.Statements.InvokeMethod.MethodName%2A>|True|Der Name der Methode, die bei Ausführung der Aktivität aufgerufen werden soll.Die aufgerufene Methode muss als **public**\-Methode deklariert worden sein.Diese Eigenschaft kann in der Designeroberfläche bearbeitet werden.Dies ist eine obligatorische Eigenschaft.|  
|<xref:System.Activities.Statements.InvokeMethod.Parameters%2A>|False|Die Parameterauflistung der aufgerufenen Methode.Die Parameter müssen der Auflistung in derselben Reihenfolge wie in der Methodensignatur hinzugefügt werden.Klicken Sie im Eigenschaftenraster im **Parameters**\-Feld auf die Schaltfläche mit den Auslassungspunkten. Daraufhin wird das Dialogfeld **Parameter** angezeigt, in dem Sie diese Eigenschaft festlegen können.Klicken Sie auf die Schaltfläche **Argument erstellen**, um die Parameter hinzuzufügen.|  
|<xref:System.Activities.Statements.InvokeMethod.Result%2A>|False|Der Rückgabewert des Methodenaufrufs.|  
|<xref:System.Activities.Statements.InvokeMethod.RunAsynchronously%2A>|True|Gibt an, ob die Methode asynchron aufgerufen wird.Der Standardwert ist **False**.|  
|<xref:System.Activities.Statements.InvokeMethod.TargetObject%2A>|False|Das Objekt, das die aufzurufende Methode enthält.Diese Eigenschaft kann in der Designeroberfläche bearbeitet werden.<br /><br /> Es muss entweder das <xref:System.Activities.Statements.InvokeMethod.TargetObject%2A>\-Objekt oder der <xref:System.Activities.Statements.InvokeMethod.TargetType%2A>\-Typ festgelegt werden.|  
|<xref:System.Activities.Statements.InvokeMethod.TargetType%2A>|False|Der Typ des <xref:System.Activities.Statements.InvokeMethod.TargetObject%2A>\-Objekts.Diese Eigenschaft kann in der Designeroberfläche bearbeitet werden.Diese Eigenschaft muss nur festgelegt werden, wenn die aufgerufene Methode statisch ist.|  
  
 Um Parameter als **out**\-Parameter in C\# \(z. B. `Method1(out myParam)),`\) zu übergeben, sollten Sie **OutArgument** statt **InOutArgument** verwenden.  
  
 Methoden mit Argumenten namens **TargetObject** oder **Result** können nicht mit der <xref:System.Activities.Statements.InvokeMethod>\-Aktivität aufgerufen werden.Der Grund dafür ist, dass die <xref:System.Activities.Statements.InvokeMethod>\-Aktivität <xref:System.Activities.Statements.InvokeMethod.GenericTypeArguments%2A>, <xref:System.Activities.Statements.InvokeMethod.TargetObject%2A> und <xref:System.Activities.Statements.InvokeMethod.Result%2A> in <xref:System.Activities.Activity.CacheMetadata%2A> registriert.  
  
 Der Algorithmus zum Registrieren der Parameter in <xref:System.Activities.Activity.CacheMetadata%2A> wird in der folgenden Liste dargestellt:  
  
1.  Registrieren Sie das <xref:System.Activities.Statements.InvokeMethod.TargetObject%2A>\-Argument.  
  
2.  Registrieren Sie das <xref:System.Activities.Statements.InvokeMethod.Result%2A>\-Argument.  
  
3.  Durchlaufen Sie die <xref:System.Activities.Statements.InvokeMethod.Parameters%2A>\-Auflistung, und registrieren Sie jedes Argument.  
  
 Die resultierende Ausnahme hat den Typ <xref:System.Activities.InvalidWorkflowException> mit der folgenden Meldung: 'InvokeMethod': Eine Variable, RuntimeArgument oder ein DelegateArgument ist bereits mit dem Namen 'TargetObject' vorhanden.Namen müssen innerhalb einer Umgebung eindeutig sein.  
  
 Diese Einschränkung gilt nicht für <xref:System.Activities.Statements.InvokeMethod.TargetType%2A> und <xref:System.Activities.Statements.InvokeMethod.RunAsynchronously%2A>, da sie keine Workflowargumente sind und daher nicht in der <xref:System.Activities.Statements.InvokeMethod.GenericTypeArguments%2A>\-Auflistung der <xref:System.Activities.Statements.InvokeMethod>\-Aktivität in der <xref:System.Activities.Activity.CacheMetadata%2A>\-Methode registriert werden.  
  
## Siehe auch  
 [Primitive](../workflow-designer/primitives-activity-designers.md)   
 [Assign](../workflow-designer/assign-activity-designer.md)   
 [Delay](../workflow-designer/delay-activity-designer.md)   
 [WriteLine](../workflow-designer/writeline-activity-designer.md)