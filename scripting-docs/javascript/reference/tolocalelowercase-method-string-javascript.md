---
title: "toLocaleLowerCase-Methode (String) (JavaScript) | Microsoft Docs"
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
  - "toLocaleLowerCase"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "toLocaleLowerCase-Methode"
ms.assetid: add894d3-d14a-4dbc-a9b9-7ad1d3a2e581
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# toLocaleLowerCase-Methode (String) (JavaScript)
Konvertiert alle alphabetischen Zeichen unter Berücksichtigung des aktuellen Gebietsschemas der Hostumgebung in Kleinbuchstaben.  
  
## Syntax  
  
```  
  
stringVar.toLocaleLowerCase( )  
```  
  
## Hinweise  
 Der erforderliche `stringVar`\-Verweis ist ein `String`\-Objekt oder Zeichenfolgenliteral.  
  
 Die `toLocaleLowerCase`\-Methode konvertiert die Zeichen in einer Zeichenfolge unter Berücksichtigung des aktuellen Gebietsschemas der Hostumgebung.  In den meisten Fällen wird dasselbe Ergebnis erzielt wie mit der `toLowerCase`\-Methode.  Die Ergebnisse sind unterschiedlich, wenn die Regeln für eine Sprache mit den regulären Unicodezuordnungen der Groß\-\/Kleinschreibung in Konflikt stehen.  
  
## Anforderungen  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
 **Gilt für**: [String\-Objekt](../../javascript/reference/string-object-javascript.md)  
  
## Siehe auch  
 [toLocaleUpperCase\-Methode \(String\)](../../javascript/reference/tolocaleuppercase-method-string-javascript.md)   
 [toLowerCase\-Methode](../../javascript/reference/tolowercase-method-javascript.md)