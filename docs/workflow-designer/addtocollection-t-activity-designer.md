---
title: "AddToCollection&lt;T&gt;-Aktivit&#228;tsdesigner | Microsoft Docs"
ms.custom: ""
ms.date: "09/21/2016"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "System.Activities.Statements.AddToCollection`1.UI"
ms.assetid: f7fc0702-164e-4370-8946-bb2f9f9384b7
caps.latest.revision: 5
caps.handback.revision: 5
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
---
# AddToCollection&lt;T&gt;-Aktivit&#228;tsdesigner
Der **AddToCollection\<T\>**\-Aktivitätsdesigner wird verwendet, um eine <xref:System.Activities.Statements.AddToCollection%601>\-Aktivität zu erstellen und zu konfigurieren.  
  
## Die AddToCollection\<T\>\-Aktivität  
 Die <xref:System.Activities.Statements.AddToCollection%601>\-Aktivität fügt einer Auflistung ein Element hinzu.  
  
### Verwenden des AddToCollection\<T\>\-Aktivitätsdesigners  
 Der **AddToCollection\<T\>**\-Aktivitätsdesigner befindet sich in der Kategorie **Auflistung** der **Toolbox**, auf die Sie zugreifen können, indem Sie in [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] auf die Registerkarte **Toolbox** klicken \(Sie können auch im Menü **Ansicht** den Befehl **Symbolleiste** auswählen oder STRG\+ALT\+X drücken\).  
  
 Der **AddToCollection\<T\>**\-Aktivitätsdesigner kann aus der **Toolbox** gezogen und auf der [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] Oberfläche dort abgelegt werden, wo Aktivitätsdesigner normalerweise platziert werden, etwa innerhalb einer <xref:System.Activities.Statements.Sequence>.Dadurch wird eine <xref:System.Activities.Statements.AddToCollection%601>\-Aktivität mit dem standardmäßigen <xref:System.Activities.Activity.DisplayName%2A> AddToCollection\<Int32\> erstellt.\(Der *TypeArgument*\-Standardwert ist **Int32**.Dies kann im Eigenschaftenraster geändert werden.\) Der <xref:System.Activities.Activity.DisplayName%2A>\-Wert kann im Header des **AddToCollection\<T\>**\-Aktivitätsdesigners oder im Feld **DisplayName** des Eigenschaftenrasters bearbeitet werden.Die anderen Eigenschaften müssen im Eigenschaftenraster bearbeitet werden.  
  
### Die AddToCollection\-\<T\>\-Eigenschaften  
 In der folgenden Tabelle werden die Eigenschaften von <xref:System.Activities.Statements.AddToCollection%601> gezeigt, und es wird beschrieben, wie sie im Designer verwendet werden.  
  
|Eigenschaftenname|Erforderlich|Verwendung|  
|-----------------------|------------------|----------------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|Gibt den benutzerfreundlichen Namen der <xref:System.Activities.Statements.AddToCollection%601>\-Aktivität an.Der Standardname lautet AddToCollection\<Int32\>.Obwohl der <xref:System.Activities.Activity.DisplayName%2A>\-Wert nicht zwingend erforderlich ist, wird empfohlen, einen Anzeigenamen zu verwenden.|  
|<xref:System.Activities.Statements.AddToCollection%601.Item%2A>|True|Das Element, das der Collection \<T\> hinzugefügt werden soll.Dieses Element hat den Typ *T*, der Typ, den *TypeArgument* besitzt.Geben Sie im Eigenschaftenraster einen Visual Basic\-Ausdruck ein, um das Element anzugeben.|  
|<xref:System.Activities.Statements.AddToCollection%601.Collection%2A>|True|Die Auflistung, zu der das Element hinzugefügt werden soll.Diese Auflistung hat den Typ **ICollection\<TypeArgument\>**.Geben Sie im Eigenschaftenraster einen Visual Basic\-Ausdruck ein, um die Auflistung anzugeben.|  
|*TypeArgument*|True|Der Typ T der in der <xref:System.Collections.Generic.ICollection%601> enthaltenen Elemente.Standardmäßig ist der *TypeArgument*\-Typ auf **Int32** festgelegt.Sie ändern den Typ von *TypeArgument*, indem Sie im Kombinationsfeld des Eigenschaftenrasters einen anderen Wert auswählen.|  
  
## Siehe auch  
 [Auflistung](../workflow-designer/collection-activity-designers.md)   
 [AddToCollection\<T\> Activity Designer](../workflow-designer/addtocollection-t-activity-designer.md)   
 [ClearCollection\<T\>](../workflow-designer/clearcollection-t-activity-designer.md)   
 [ExistsInCollection\<T\>](../workflow-designer/existsincollection-t-activity-designer.md)   
 [RemoveFromCollection\<T\>](../workflow-designer/removefromcollection-t-activity-designer.md)