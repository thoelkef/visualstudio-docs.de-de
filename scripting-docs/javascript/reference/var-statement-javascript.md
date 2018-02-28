---
title: Var-Anweisung (JavaScript) | Microsoft Docs
ms.custom: 
ms.date: 01/22/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- var_JavaScriptKeyword
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- declaring variables, var statement
- var statement
ms.assetid: 56f900af-a5c4-4667-9664-5956d30f0aae
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 839b6904fa59b6f4ea9a5c4d8e00213cd351517a
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="var-statement-javascript"></a>var-Anweisung (JavaScript)
Deklariert eine Variable.  
  
## <a name="syntax"></a>Syntax  
  
```  
var variable1 = value1  
```  
  
## <a name="parameters"></a>Parameter  
 `variable1`  
 Der Name der Variablen, die deklariert wird.  
  
 `value1`  
 Die Startwerte, die den Variablen zugewiesen sind.  
  
## <a name="remarks"></a>Hinweise  
 Verwenden der `var` Anweisung, um Variablen zu deklarieren. Den Variablen können in der Deklaration oder später im Skript Werte zugewiesen werden.  
  
 Eine Variable wird erstmalig deklariert, wird Sie in das Skript.  
  
 Sie können eine Variable deklarieren, ohne die `var` -Schlüsselwort und weisen Sie einen Wert zu. Dies bezeichnet man eine *impliziten Deklaration*, und es wird nicht empfohlen. Eine implizite Deklaration gibt den globalen Gültigkeitsbereich den Variablen. Wenn Sie eine Variable auf Prozedurebene deklarieren, jedoch sollen in der Regel nicht es einen globalen Gültigkeitsbereich haben. Verwenden Sie zur Vermeidung, erteilen den globalen Gültigkeitsbereich den Variablen, die `var` Schlüsselwort in der Variablendeklaration.  
  
 Wenn Sie die Variable in der `var`-Anweisung nicht initialisieren, wird ihr automatisch der [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]-Wert `undefined` zugewiesen.  
  
## <a name="example"></a>Beispiel  
 Die folgenden Beispiele veranschaulichen die Verwendung der `var` Anweisung.  
  
```JavaScript  
var index;  
var name = "Thomas Jefferson";  
var answer = 42, counter, numpages = 10;  
var myarray = new Array();  
```  
  
## <a name="requirements"></a>Anforderungen  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>Siehe auch  
 [Function-Anweisung](../../javascript/reference/function-statement-javascript.md)   
 [new-Operator](../../javascript/reference/new-operator-decrementjavascript.md)   
 [Array-Objekt](../../javascript/reference/array-object-javascript.md)   
 [Variablen](../../javascript/variables-javascript.md)