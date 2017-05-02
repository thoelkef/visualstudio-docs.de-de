---
title: "if...else-Anweisung (JavaScript) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-javascript"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "else_JavaScriptKeyword"
  - "if_JavaScriptKeyword"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "if-Anweisung, if...else"
  - "Schleifenstruktur, if...else-Anweisungen"
ms.assetid: dfbe86e8-9c1e-4ef5-bb9c-7d1db7ce2506
caps.latest.revision: 18
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 16
---
# if...else-Anweisung (JavaScript)
Führt bedingt eine Gruppe von Anweisungen aus, abhängig vom Wert eines Ausdrucks.  
  
## Syntax  
  
```  
if (condition1) {  
    statement1  
}  
[else if (condition2) {  
    statement2  
}]  
[else {  
    statement3]   
}]  
```  
  
## Parameter  
 `condition1`  
 Erforderlich.  Ein boolescher Ausdruck.  Wenn `condition1` `null` oder `undefined` ist, wird `condition1` als `false` behandelt.  
  
 `statement1`  
 Optional.  Die auszuführende Anweisung, wenn `condition1` den Wert **true** hat.  Hierbei kann es sich um eine Verbundanweisung handeln.  
  
 `condition2`  
 Die auszuwertende Bedingung.  
  
 `statement2`  
 Optional.  Die auszuführende Anweisung, wenn `condition2` den Wert `true` hat.  Hierbei kann es sich um eine Verbundanweisung handeln.  
  
 `statement3`  
 Wenn `condition1` und `condition2` den Wert `false` haben, wird diese Anweisung ausgeführt.  
  
## Beispiel  
 Im folgenden Code wird die Verwendung von `if`, `if else` und `else` veranschaulicht.  
  
 Im Allgemeinen ist es sinnvoll, `statement1` und `statement2` zur besseren Übersicht und zur Vermeidung von unbeabsichtigten Fehlern in geschweifte Klammern \({}\) zu setzen.  
  
```javascript  
var z = 3;  
if (x == 5) {  
    z = 10;  
}  
else if (x == 10) {  
    z = 15;  
}  
else {  
    z = 20;  
}  
```  
  
## Anforderungen  
 [!INCLUDE[jsv1](../../includes/jsv1-md.md)]  
  
## Siehe auch  
 [Bedingter \(ternärer\) Operator \(?:\)](../../javascript/reference/conditional-ternary-operator-decrement-javascript.md)