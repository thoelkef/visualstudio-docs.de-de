---
title: Delete-Operator (JavaScript) | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: delete_JavaScriptKeyword
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- array elements, deleting
- properties, deleting
- delete operator
ms.assetid: 55c6487e-96ea-455b-a7ed-dc35c41ac2f3
caps.latest.revision: "16"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ee3def1977c0b29ee14ebf836f2d9ebb51d5a5ef
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="delete-operator-javascript"></a>delete-Operator (JavaScript)
Löscht eine Eigenschaft aus einem Objekt oder entfernt ein Element aus einem Array.  
  
## <a name="syntax"></a>Syntax  
  
```  
delete expression  
```  
  
## <a name="remarks"></a>Hinweise  
 Die `expression` Argument ist ein gültiger [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] verursacht Ausdruck, der normalerweise ein Eigenschaftenelement für Namen oder Array.  
  
 Wenn das Ergebnis des `expression` ist ein Objekt, in die angegebene Eigenschaft `expression` vorhanden ist, und das Objekt wird nicht gelöscht werden soll, `false` wird zurückgegeben.  
  
 In allen anderen Fällen `true` zurückgegeben wird.  
  
## <a name="example"></a>Beispiel  
 Das folgende Beispiel zeigt, wie ein Element aus einem Array zu entfernen.  
  
```JavaScript  
// Create an array.  
var ar = new Array (10, 11, 12, 13, 14);  
  
// Remove an element from the array.  
delete ar[1];  
  
// Print the results.  
document.write ("element 1: " + ar[1]);  
document.write ("<br />");  
document.write ("array: " + ar);  
// Output:  
//  element 1: undefined  
//  array: 10,,12,13,14  
```  
  
## <a name="example"></a>Beispiel  
 Im folgende Beispiel wird gezeigt, wie Eigenschaften aus einem Objekt gelöscht wird.  
  
```JavaScript  
// Create an object and add expando properties.  
var myObj = new Object();  
myObj.name = "Fred";  
myObj.count = 42;  
  
// Delete the properties from the object.  
delete myObj.name;  
delete myObj["count"];  
  
// Print the results.  
document.write ("name: " + myObj.name);  
document.write ("<br />");  
document.write ("count: " + myObj.count);  
// Output:  
//  name: undefined  
//  count: undefined  
```  
  
## <a name="requirements"></a>Anforderungen  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
## <a name="see-also"></a>Siehe auch  
 [Operatorrangfolge](../../javascript/operator-subtractprecedence-javascript.md)   
 [Zusammenfassung der Operatoren (JavaScript)](../../javascript/misc/operator-subtractsummary-javascript.md)