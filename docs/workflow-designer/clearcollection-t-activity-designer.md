---
title: "ClearCollection&lt;T&gt;-Aktivit&#228;tsdesigner | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "System.Activities.Statements.ClearCollection`1.UI"
ms.assetid: db0e5da2-7b5a-4f1a-864c-f3aeeeeb51a7
caps.latest.revision: 7
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 7
---
# ClearCollection&lt;T&gt;-Aktivit&#228;tsdesigner
Der **ClearCollection\<T\>**\-Aktivitätsdesigner wird verwendet, um eine <xref:System.Activities.Statements.ClearCollection%601>\-Aktivität zu erstellen und zu konfigurieren.  
  
## Die ClearCollection\<T\>\-Aktivität  
 Die <xref:System.Activities.Statements.ClearCollection%601>\-Aktivität löscht alle Elemente einer angegebenen Auflistung.  
  
### Verwenden des ClearCollection\<T\>\-Aktivitätsdesigners  
 Der **ClearCollection\<T\>**\-Aktivitätsdesigner befindet sich in der Kategorie **Auflistung** der **Toolbox**, auf die Sie zugreifen können, indem Sie in [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] auf die Registerkarte **Toolbox** klicken \(Sie können auch im Menü **Ansicht** den Befehl **Symbolleiste** auswählen oder STRG\+ALT\+X drücken\).  
  
 Der **ClearCollection\<T\>**\-Aktivitätsdesigner kann aus der **Toolbox** gezogen und auf der [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)]\-Oberfläche dort abgelegt werden, wo Aktivitätsdesigner normalerweise platziert werden, z. B. in einer <xref:System.Activities.Statements.Sequence>.Dadurch wird eine <xref:System.Activities.Statements.ClearCollection%601>\-Aktivität mit dem standardmäßigen <xref:System.Activities.Activity.DisplayName%2A> ClearCollection\<Int32\> erstellt.\(Der *TypeArgument*\-Standardwert ist **Int32**.Dies kann im Eigenschaftenraster geändert werden.\) Der <xref:System.Activities.Activity.DisplayName%2A>\-Wert kann im Header des **ClearCollection\<T\>**\-Aktivitätsdesigners oder im Feld **DisplayName** des Eigenschaftenrasters bearbeitet werden.Die anderen Eigenschaften müssen im Eigenschaftenraster bearbeitet werden.  
  
### Die ClearCollection\<T\>\-Eigenschaften  
 In der folgenden Tabelle werden die Eigenschaften von <xref:System.Activities.Statements.ClearCollection%601> gezeigt, und es wird beschrieben, wie sie im Designer verwendet werden.  
  
|Eigenschaftenname|Erforderlich|Verwendung|  
|-----------------------|------------------|----------------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|Gibt den optionalen Anzeigenamen der <xref:System.Activities.Statements.ClearCollection%601>\-Aktivität an.Der Standardname lautet ClearCollection\<Int32\>.Obwohl der <xref:System.Activities.Activity.DisplayName%2A>\-Wert nicht zwingend erforderlich ist, wird empfohlen, einen Anzeigenamen zu verwenden.|  
|<xref:System.Activities.Statements.ClearCollection%601.Collection%2A>|True|Gibt die Auflistung an, deren Elemente gelöscht werden sollen.Diese Auflistung hat den Typ **ICollection\<TypeArgument\>.** Geben Sie die Auflistung an, indem Sie einen Visual Basic\-Ausdruck im Eigenschaftenraster eingeben.|  
|*TypeArgument*|True|Gibt den Typ T der in <xref:System.Collections.Generic.ICollection%601> enthaltenen Elemente an.Standardmäßig ist der *TypeArgument*\-Typ auf **Int32** festgelegt.Sie ändern den Typ von *TypeArgument*, indem Sie im Kombinationsfeld des Eigenschaftenrasters einen anderen Wert auswählen.|  
  
## Siehe auch  
 [Auflistung](../workflow-designer/collection-activity-designers.md)   
 [AddToCollection\<T\>](../workflow-designer/addtocollection-t-activity-designer.md)   
 [ExistsInCollection\<T\>](../workflow-designer/existsincollection-t-activity-designer.md)   
 [RemoveFromCollection\<T\>](../workflow-designer/removefromcollection-t-activity-designer.md)