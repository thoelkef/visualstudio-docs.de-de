---
title: "Die Arrayl&#228;nge muss eine endliche positive ganze Zahl sein | Microsoft Docs"
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
  - "VS.WebClient.Help.SCRIPT5029"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: 1a467040-4702-4178-848f-418a5974e907
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# Die Arrayl&#228;nge muss eine endliche positive ganze Zahl sein
Sie rufen den **Array** \-Konstruktor mit einem Argument auf, das keine ganze Zahl ist \(ganze Zahlen bestehen aus null plus dem Satz von positiven ganzen Zahlen\).  
  
### So beheben Sie diesen Fehler  
  
-   Verwenden Sie positive ganze Zahlen nur, wenn Sie ein neues `Array`\-Objekt erstellen.  Wenn Sie ein Array mit einem einzelnen Element erstellen möchten, die keine ganze Zahl ist, führen Sie dies in einem zwei Schritte umfassenden Prozess aus.  Erstellen Sie zunächst ein Array mit einem Element, und speichern Sie dann den Wert im ersten Element \(array\[0\]\).  Durch folgenden Code wird z. B. dieser Fehler verursacht.  
  
    ```javascript  
    var piArray = new Array(3.14159);  
    ```  
  
     Im folgenden Beispiel wird die richtige Methode dargestellt, ein Array mit einem einzelnen numerischen Element anzugeben.  
  
    ```javascript  
    var piArray = new Array(1);  
    piArray [0] = 3.14159;  
    ```  
  
     Es gibt keine Obergrenze für die Größe eines Arrays, außer den maximalen ganzzahligen Wert \(ungefähr 4 Milliarden\).  
  
## Siehe auch  
 [Verwenden von Arrays](../../javascript/advanced/using-arrays-javascript.md)