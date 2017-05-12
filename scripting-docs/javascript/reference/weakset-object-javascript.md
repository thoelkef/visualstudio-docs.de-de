---
title: "WeakSet-Objekt (JavaScript) | Microsoft Docs"
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
ms.assetid: f97e6e7c-d678-4e32-978e-d949a7cafa3a
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# WeakSet-Objekt (JavaScript)
Eine Auflistung eindeutiger Objekte eines beliebigen Typs.  
  
## Syntax  
  
```  
setObj = new WeakSet()  
```  
  
## Hinweise  
 Wenn Sie versuchen, ein nicht eindeutiges Objekt zu `WeakSet` hinzuzufügen, wird das neue Objekt nicht der Auflistung hinzugefügt.  
  
 Im Gegensatz zu einem `Set` dürfen der Auflistung nur Objekte hinzugefügt werden.  Willkürliche Werte können nicht der Auflistung hinzugefügt werden.  
  
 Bei einem `WeakSet`\-Objekt werden Objekte im Satz schwach referenziert.  Dies bedeutet, dass `WeakSet` die Ausführung einer Garbage Collection für die Objekte nicht verhindert.  Wenn \(außer `WeakSet`\) keine Verweise auf die Objekte vorhanden sind, kann der Garbage Collector die Objekte erfassen.  
  
 `WeakSet` \(oder `WeakMap`\) kann in einigen Szenarien im Zusammenhang mit dem Zwischenspeichern von Objekten oder Objektmetadaten im Cache hilfreich sein.  Beispielsweise können Metadaten für nicht erweiterbare Objekte in einem `WeakSet` gespeichert werden. Sie können auch mit `WeakSet` einen Cache von Benutzerimages erstellen.  
  
## Eigenschaften  
 In der folgenden Tabelle werden die Eigenschaften des `WeakSet`\-Objekts aufgelistet.  
  
|Eigenschaft|Beschreibung|  
|-----------------|------------------|  
|Konstruktor|Gibt die Funktion an, durch die ein Satz erstellt wird.|  
|Prototyp|Gibt einen Verweis auf den Prototyp für einen Satz zurück.|  
  
## Methoden  
 In der folgenden Tabelle werden die Methoden des `WeakSet`\-Objekts aufgelistet.  
  
|Methode|Beschreibung|  
|-------------|------------------|  
|Hinzufügen|Fügt einem Satz ein Element hinzu.|  
|Löschen|Entfernt ein angegebenes Element aus einem Satz.|  
|has|Gibt `true` zurück, wenn der Satz ein angegebenes Element enthält.|  
  
## Beispiel  
 Im folgenden Beispiel wird gezeigt, wie Sie einem Satz Member hinzufügen und dann prüfen, ob sie hinzugefügt wurden.  
  
```javascript  
var ws = new WeakSet();  
  
var str = new String("Thomas Jefferson");  
var num = new Number(1776);  
  
ws.add(str);  
ws.add(num);  
  
console.log(ws.has(str));  
console.log(ws.has(num));  
  
ws.delete(str);  
console.log(ws.has(str));  
  
// Output:  
// true  
// true  
// false  
```  
  
## Anforderungen  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]