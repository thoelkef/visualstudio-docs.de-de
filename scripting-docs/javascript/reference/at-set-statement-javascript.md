---
title: "@set-Anweisung (JavaScript) | Microsoft Docs"
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
  - "@set_JavaScriptKeyword"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "@set-Anweisung"
  - "Bedingte Kompilierung, Variablen"
ms.assetid: 36f15926-3e69-422d-82a2-d186dc088203
caps.latest.revision: 14
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 14
---
# @set-Anweisung (JavaScript)
Erstellt Variablen, die in bedingten Kompilierungsanweisungen verwendet werden.  
  
> [!WARNING]
>  Die bedingte Kompilierung wird im Standardmodus von Internet Explorer 11 und den [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)]\-Apps nicht unterstützt.  Die bedingte Kompilierung wird im Standardmodus von Internet Explorer 10 und allen früheren Versionen unterstützt.  
  
## Syntax  
  
```  
  
@set @varname = term   
```  
  
## Parameter  
 *varname*  
 Erforderlich.  Gültiger [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]\-Variablenname.  Dem Namen muss stets das Zeichen "@" vorangestellt sein.  
  
 `term`  
 Erforderlich.  Keine unäre Operatoren oder mehrere unäre Operatoren, auf die eine Konstante, eine bedingte Kompilierungsvariable oder ein in Klammern gesetzter Ausdruck folgt.  
  
## Hinweise  
 Numerische und boolesche Variablen werden bei der bedingten Kompilierung unterstützt.  Zeichenfolgen werden nicht unterstützt.  Unter Verwendung von `@set` erstellte Variablen werden hauptsächlich in Anweisungen für bedingte Kompilierungen eingesetzt. In [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]\-Code können sie jedoch an beliebigen Stellen verwendet werden.  
  
 Beispiele für Variablendeklarationen sehen wie folgt aus:  
  
```javascript  
  
        @set @myvar1 = 12  
  
@set @myvar2 = (@myvar1 * 20)  
  
@set @myvar3 = @_jscript_version  
```  
  
 Die folgenden Operatoren werden in Ausdrücken unterstützt, die in Klammern gesetzt sind:  
  
-   `!  ~`  
  
-   `* / %`  
  
-   `+ -`  
  
-   `<< >> >>>`  
  
-   `< <= > >=`  
  
-   `== != === !==`  
  
-   `& ^ |`  
  
-   `&& | |`  
  
 Wenn eine Variable verwendet wird, bevor sie definiert wurde, ist ihr Wert `NaN`.  Die Verwendung von `NaN` kann mit der `@if`\-Anweisung überprüft werden:  
  
```javascript  
@if (@newVar != @newVar)  
   ...  
```  
  
 Dies funktioniert, da `NaN` der einzige Wert ist, der ungleich sich selbst ist.  
  
## Anforderungen  
 Wird in allen Versionen von Internet Explorer, jedoch nicht in [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)]\-Apps unterstützt.  
  
## Siehe auch  
 [Bedingte Kompilierung](../../javascript/advanced/conditional-compilation-javascript.md)   
 [Variablen für die bedingte Kompilierung](../../javascript/advanced/conditional-compilation-variables-javascript.md)   
 [@cc\_on\-Anweisung](../../javascript/reference/at-cc-on-statement-javascript.md)   
 [@if\-Anweisung](../../javascript/reference/at-if-statement-javascript.md)