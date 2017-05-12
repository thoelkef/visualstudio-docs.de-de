---
title: "Objekt erwartet | Microsoft Docs"
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
  - "VS.WebClient.Help.SCRIPT5007"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: 5d88c93d-e5b5-4b11-9bb5-bf1a5e41ccc3
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# Objekt erwartet
Sie haben versucht, eine Methode oder Eigenschaft für ein Objekt aufzurufen, dessen Typ nicht `Object` lautete, oder Sie haben ein Argument übergeben, dessen Typ nicht `Object` lautete, als `Object` erforderlich war.  
  
### So beheben Sie diesen Fehler  
  
-   Rufen Sie die Methode oder Eigenschaft nur für Objekte vom Typ `Object` auf.  
  
-   Sollte der Fehler für ein Nicht\-Objekt\-Argument auftreten, übergeben Sie ein Objekt vom Typ `Object`.  
  
-   Überprüfen Sie, ob ein nicht definierter oder NULL\-Verweis anstelle eines Objekts vom Typ `Object` aufgerufen wird.  
  
     Beispiel: Angenommen dieser Fehler tritt auf myVar im folgenden Code auf:  
  
    ```javascript  
    var str = myVar.toString();  
    ```  
  
     Sie können stattdessen diesen Code verwenden:  
  
    ```javascript  
    if (myVar) {  
        var str = myVar.toString();  
    }  
    ```  
  
## Siehe auch  
 [Object\-Objekt](../../javascript/reference/object-object-javascript.md)   
 [Objekte und Arrays](../../javascript/objects-and-arrays-javascript.md)