---
title: "Der Arrayl&#228;nge muss eine endliche positive Zahl zugewiesen werden | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "javascript"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VS.WebClient.Help.SCRIPT5030"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: c51c66a4-a543-4e95-b18d-2cfbcb3d1fdd
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# Der Arrayl&#228;nge muss eine endliche positive Zahl zugewiesen werden
Beim Festlegen der **length** \-Eigenschaft eines vorhandenen **Array**\-Objekts haben Sie eine Arraylänge angegeben, die keine positive Zahl oder Null war.  Dieser Fehler tritt auf, wenn Sie einen Wert der **length**\-Eigenschaft eines `Array`\-Objekts einen Wert zuweisen, der negativ oder keine Zahl \(`NaN`\) ist.  Beachten Sie, dass [!INCLUDE[javascript](../../includes/javascript-md.md)] Bruchzahlen automatisch in ganze Zahlen konvertiert.  
  
### So beheben Sie diesen Fehler  
  
-   Weisen Sie der length\-Eigenschaft eine positive ganze Zahl zu.  Es gibt keine Obergrenze für die Größe eines Arrays, außer den maximalen ganzzahligen Wert \(ungefähr 4 Milliarden\).  Im folgenden Beispiel wird die richtige Methode zum Festlegen der **length**\-Eigenschaft eines **Array** \-Objekts dargestellt.  
  
    ```javascript  
    var my_array = new Array();  
    my_array.length = 99;  
    ```  
  
## Siehe auch  
 [Verwenden von Arrays](../../javascript/advanced/using-arrays-javascript.md)