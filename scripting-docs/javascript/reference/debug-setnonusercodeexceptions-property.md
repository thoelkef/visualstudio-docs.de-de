---
title: "Debug.setNonUserCodeExceptions-Eigenschaft | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-javascript"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: 1dd2abee-a415-41bb-a359-017da62f9485
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# Debug.setNonUserCodeExceptions-Eigenschaft
Legt fest, ob try\/catch\-Blöcke in diesem Bereich vom Debugger als "vom Benutzer unbehandelt" behandelt werden sollen.  Ausnahmen können als "ausgelöst", "vom Benutzercode unbehandelt" oder "unbehandelt" klassifiziert werden.  
  
 Wenn diese Eigenschaft in einem angegebenen Bereich auf `true` festgelegt ist, kann der Debugger bestimmte Aktionen \(beispielsweise "break"\) für Ausnahmen festlegen, die in diesem Bereich ausgelöst wurden, wenn der Entwickler bei Ausnahmen "vom Benutzercode unbehandelt" unterbrechen möchte.  Wenn diese Eigenschaft auf `false` festgelegt wird, ist das gleichbedeutend mit einer nicht festgelegten Eigenschaft.  
  
 Weitere Informationen zum Debuggen finden Sie in der [Übersicht zum Active Script\-Debugging](http://go.microsoft.com/fwlink/p/?LinkId=249469).  
  
## Syntax  
  
```  
Debug.setNonUserCodeExceptions [= bool];  
```  
  
## Beispiel  
 Mit folgendem Code kann diese Eigenschaft festgelegt werden.  
  
```javascript  
(function () {  
    Debug.setNonUserCodeExceptions = true;  
    try{  
        var x = null;  
        x.y();  
    } catch (e) {  
    // Catch the exception.  
    }  
})();  
```  
  
## Anforderungen  
 [!INCLUDE[jsv10](../../includes/jsv10-md.md)]