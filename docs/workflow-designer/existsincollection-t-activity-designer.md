---
title: "ExistsInCollection&lt;T&gt;-Aktivit&#228;tsdesigner | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "System.Activities.Statements.ExistsInCollection`1.UI"
ms.assetid: 0acf9a13-caf5-4bb4-ba22-ec37d2b7267a
caps.latest.revision: 6
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 6
---
# ExistsInCollection&lt;T&gt;-Aktivit&#228;tsdesigner
Der **ExistsInCollection\<T\>**\-Aktivitätsdesigner wird verwendet, um eine <xref:System.Activities.Statements.ExistsInCollection%601>\-Aktivität zu erstellen und zu konfigurieren.  
  
## Die ExistsInCollection\<T\>\-Aktivität  
 Mit der <xref:System.Activities.Statements.ExistsInCollection%601>\-Aktivität wird bestimmt, ob ein angegebenes Element in einer bestimmten Auflistung vorhanden ist.  
  
### Verwenden des ExistsInCollection\<T\>\-Aktivitätsdesigners  
 Der **ExistsInCollection\<T\>**\-Aktivitätsdesigner befindet sich in der Kategorie **Auflistung** der **Toolbox**, auf die Sie zugreifen, indem Sie in [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] auf die Registerkarte **Toolbox** klicken. \(Alternativ können Sie **Symbolleiste** im Menü **Ansicht** wählen oder die Tastenkombination STRG\+ALT\+X verwenden.\)  
  
 Sie können den **ExistsInCollection\<T\>**\-Aktivitätsdesigner aus der **Toolbox** auf die [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)]\-Oberfläche ziehen und ablegen, wo normalerweise Aktivitäten platziert werden, z. B. in einem <xref:System.Activities.Statements.Sequence>\-Element.Hierdurch erstellen Sie eine <xref:System.Activities.Statements.ExistsInCollection%601>\-Aktivität mit dem <xref:System.Activities.Activity.DisplayName%2A>\-Standardnamen ExistsInCollection\<Int32\>.\(Der Standardwert für *TypeArgument* ist **Int32**.Diese Einstellung kann im Eigenschaftenraster geändert werden.\)  Der <xref:System.Activities.Activity.DisplayName%2A>\-Wert kann im Header des **ExistsInCollection\<T\>**\-Aktivitätsdesigners oder im Feld **DisplayName** des Eigenschaftenrasters geändert werden.Die anderen Eigenschaften müssen im Eigenschaftenraster bearbeitet werden.  
  
### Die ExistsInCollection\<T\>\-Eigenschaften  
 Die folgende Tabelle enthält die <xref:System.Activities.Statements.ExistsInCollection%601>\-Eigenschaften und eine Beschreibung zu deren Verwendung im Designer.  
  
|Eigenschaftenname|Erforderlich|Verwendung|  
|-----------------------|------------------|----------------|  
|<xref:System.Activities.Activity.DisplayName%2A>|Nein|Der Anzeigename der <xref:System.Activities.Statements.ExistsInCollection%601>\-Aktivität.Der Standardwert ist ExistsInCollection\<Int32\>.Der <xref:System.Activities.Activity.DisplayName%2A>\-Wert ist zwar nicht unbedingt erforderlich, es wird jedoch empfohlen, diesen zu verwenden.|  
|<xref:System.Activities.Statements.ExistsInCollection%601.Item%2A>|Ja|Das Element, das der Auflistung \(Collection\<T\>\) hinzugefügt werden soll.Dieses Element weist den *TypeArgument*\-Typ *T* auf.Zum Angeben des Elements geben Sie im Eigenschaftenraster einen Visual Basic\-Ausdruck ein.|  
|<xref:System.Activities.Statements.ExistsInCollection%601.Collection%2A>|Ja|Die Auflistung, der das Element hinzugefügt werden soll.Diese Auflistung ist vom Typ **ICollection\<TypeArgument\>.** Zum Angeben der Auflistung geben Sie im Eigenschaftenraster einen Visual Basic\-Ausdruck ein.|  
|*TypeArgument*|True|Der Typ T der in der <xref:System.Collections.Generic.ICollection%601> enthaltenen Elemente.Standardmäßig ist der *TypeArgument*\-Typ auf **Int32** festgelegt.Zum Ändern des Typs müssen Sie im Eigenschaftenraster den Wert für *TypeArgument* im Kombinationsfeld ändern.|  
|<xref:System.Activities.Activity%601.Result%2A>|Nein|Ein Wert, der angibt, ob das angegebene Element in der Auflistung vorhanden ist.Um eine Variable anzugeben, die an das Ergebnis gebunden wird, geben Sie im Eigenschaftenraster eine Visual Basic\-Variable ein.|  
  
## Siehe auch  
 [Auflistung](../workflow-designer/collection-activity-designers.md)   
 [AddToCollection\<T\>](../workflow-designer/addtocollection-t-activity-designer.md)   
 [ClearCollection\<T\>](../workflow-designer/clearcollection-t-activity-designer.md)   
 [RemoveFromCollection\<T\>](../workflow-designer/removefromcollection-t-activity-designer.md)