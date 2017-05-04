---
title: "new-Operator (JavaScript) | Microsoft Docs"
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
  - "new_JavaScriptKeyword"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "new-Operator in JavaScript"
ms.assetid: 5ea556ba-7ae6-426c-8430-9032eee5a0a5
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# new-Operator (JavaScript)
Erstellt ein neues Objekt.  
  
## Syntax  
  
```  
new constructor ([arguments])   
```  
  
## Parameter  
 `constructor`  
 Erforderlich.  Der Konstruktor des Objekts.  Die Klammern können weggelassen werden, wenn der Konstruktor keine Argumente benötigt.  
  
 `arguments`  
 Optional.  Argumente, die an den Konstruktor des neuen Objekts übergeben werden.  
  
## Hinweise  
 Der `new`\-Operator erfüllt die folgenden Aufgaben:  
  
-   Er erstellt ein Objekt ohne Member.  
  
-   Er ruft den Konstruktor für dieses Objekt auf und übergibt als `this`\-Zeiger einen Zeiger auf das neu erstellte Objekt.  
  
-   Anschließend wird das Objekt entsprechend den an den Konstruktor übergebenen Argumenten initialisiert.  
  
 Es folgen Beispiele für die zulässige Verwendung des Operators **new**.  
  
```javascript  
my_object = new Object;  
my_array = new Array();  
my_date = new Date("Jan 5 1996");  
```  
  
## Anforderungen  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## Siehe auch  
 [function\-Anweisung](../../javascript/reference/function-statement-javascript.md)