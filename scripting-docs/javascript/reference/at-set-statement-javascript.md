---
title: '@setAnweisung (JavaScript) | Microsoft Docs'
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- '@set_JavaScriptKeyword'
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- '@set statement'
- conditional compilation, variables
ms.assetid: 36f15926-3e69-422d-82a2-d186dc088203
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 10f74a1d57a61d78897b660812a6fd8078244b6b
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="set-statement-javascript"></a>@setAnweisung (JavaScript)
Erstellt Variablen, die in bedingten Kompilierungsanweisungen verwendet werden.  
  
> [!WARNING]
>  Die bedingte Kompilierung wird im Standardmodus von Internet Explorer 11 und den [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)]-Apps nicht unterstützt. Die bedingte Kompilierung wird im Standardmodus von Internet Explorer 10 und allen früheren Versionen unterstützt.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
@set @varname = term   
```  
  
## <a name="parameters"></a>Parameter  
 *Variablenname*  
 Erforderlich. Gültiger [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]-Variablenname. Dem Namen muss stets das Zeichen "@" vorangestellt sein.  
  
 `term`  
 Erforderlich. Keine unäre Operatoren oder mehrere unäre Operatoren, auf die eine Konstante, eine bedingte Kompilierungsvariable oder ein in Klammern gesetzter Ausdruck folgt.  
  
## <a name="remarks"></a>Hinweise  
 Numerische und boolesche Variablen werden bei der bedingten Kompilierung unterstützt. Zeichenfolgen werden nicht unterstützt. Unter Verwendung von `@set` erstellte Variablen werden hauptsächlich in Anweisungen für bedingte Kompilierungen eingesetzt. In [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]-Code können sie jedoch an beliebigen Stellen verwendet werden.  
  
 Beispiele für Variablendeklarationen sehen wie folgt aus:  
  
```JavaScript  
  
      @set @myvar1 = 12  
  
@set @myvar2 = (@myvar1 * 20)  
  
@set @myvar3 = @_jscript_version  
```  
  
 Die folgenden Operatoren werden in Ausdrücken unterstützt, die in Klammern gesetzt sind:  
  
-   `! ~`  
  
-   `* / %`  
  
-   `+ -`  
  
-   `<< >> >>>`  
  
-   `< <= > >=`  
  
-   `== != === !==`  
  
-   `& ^ |`  
  
-   `&& | |`  
  
 Wenn eine Variable verwendet wird, bevor sie definiert wurde, ist ihr Wert `NaN`. Die Verwendung von `NaN` kann mit der `@if`-Anweisung überprüft werden:  
  
```JavaScript  
@if (@newVar != @newVar)  
   ...  
```  
  
 Dies funktioniert, da `NaN` der einzige Wert ist, der ungleich sich selbst ist.  
  
## <a name="requirements"></a>Anforderungen  
 Wird in allen Versionen von Internet Explorer, jedoch nicht in [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)]-Apps unterstützt.  
  
## <a name="see-also"></a>Siehe auch  
 [Bedingte Kompilierung](../../javascript/advanced/conditional-compilation-javascript.md)   
 [Variablen für die bedingte Kompilierung](../../javascript/advanced/conditional-compilation-variables-javascript.md)   
 [@cc_onAnweisung](../../javascript/reference/at-cc-on-statement-javascript.md)   
 [@if-Anweisung](../../javascript/reference/at-if-statement-javascript.md)