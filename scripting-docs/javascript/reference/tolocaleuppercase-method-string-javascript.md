---
title: "toLocaleUpperCase-Methode (String) (JavaScript) | Microsoft Docs"
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
  - "toLocaleUpperCase"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "toLocaleUpperCase-Methode"
ms.assetid: e927adb6-475e-44b2-91f7-cedda10a39b0
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# toLocaleUpperCase-Methode (String) (JavaScript)
Gibt eine Zeichenfolge zurück, in der alle alphabetischen Zeichen unter Berücksichtigung des aktuellen Gebietsschemas der Hostumgebung in Großbuchstaben konvertiert wurden.  
  
## Syntax  
  
```  
  
stringVar.toLocaleUpperCase( )  
```  
  
## Hinweise  
 Der erforderliche `stringVar`\-Verweis ist ein `String`\-Objekt oder Zeichenfolgenliteral.  
  
 Die `toLocaleUpperCase`\-Methode konvertiert die Zeichen in einer Zeichenfolge unter Berücksichtigung des aktuellen Gebietsschemas der Hostumgebung.  In den meisten Fällen ist das Ergebnis dasselbe wie das der `toUpperCase`\-Methode.  Die Ergebnisse sind unterschiedlich, wenn die Regeln für eine Sprache mit den regulären Unicodezuordnungen der Groß\-\/Kleinschreibung in Konflikt stehen.  
  
## Anforderungen  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
 **Gilt für**: [String\-Objekt](../../javascript/reference/string-object-javascript.md)  
  
## Siehe auch  
 [toLocaleLowerCase\-Methode \(String\)](../../javascript/reference/tolocalelowercase-method-string-javascript.md)   
 [toUpperCase\-Methode \(String\)](../../javascript/reference/touppercase-method-string-javascript.md)