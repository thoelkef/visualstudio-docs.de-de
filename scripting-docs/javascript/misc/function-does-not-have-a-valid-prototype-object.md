---
title: "Die Funktion hat kein g&#252;ltiges Prototypobjekt | Microsoft Docs"
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
  - "VS.WebClient.Help.SCRIPT5023"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: b9e34652-190f-4b57-b253-df2e8c4d09c6
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# Die Funktion hat kein g&#252;ltiges Prototypobjekt
Sie haben versucht, mithilfe von **instanceof** zu bestimmen, ob ein Objekt von einer bestimmten Funktionsklasse abgeleitet wurde. Jedoch wurde die `prototype`\-Eigenschaft des Objekts entweder als `null` oder als externer Objekttyp im Code neu definiert. Beides sind keine gültigen [!INCLUDE[javascript](../../includes/javascript-md.md)]\-Objekte.  Ein externes Objekt kann entweder ein Objekt aus dem Hostobjektmodell \(z. B. ein Dokumentobjekt oder Fensterobjekt von Internet Explorer\) oder ein externes COM\-Objekt sein.  
  
### So beheben Sie diesen Fehler  
  
-   Stellen Sie sicher, dass die `prototype`\-Eigenschaft der Funktion auf ein gültiges [!INCLUDE[javascript](../../includes/javascript-md.md)]\-Objekt verweist.  
  
## Siehe auch  
 [Function\-Objekt](../../javascript/reference/function-object-javascript.md)   
 [prototype\-Eigenschaft \(Objekt\)](../../javascript/reference/prototype-property-object-javascript.md)