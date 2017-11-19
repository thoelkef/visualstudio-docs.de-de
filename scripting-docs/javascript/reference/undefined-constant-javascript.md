---
title: undefined-Konstante (JavaScript) | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: undefined
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords: undefined property
ms.assetid: 2a689d7d-00b0-48fb-9c95-5c2867bde006
caps.latest.revision: "20"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8ba7fa8b160e4f5d954c8d6545da5fae41c2f74b
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="undefined-constant-javascript"></a>nicht definierte Konstante (JavaScript)
Ein Wert, der nie, z. B. eine Variable definiert wurde, der nicht initialisiert wurde.  
  
## <a name="syntax"></a>Syntax  
  
```  
undefined  
```  
  
## <a name="remarks"></a>Hinweise  
 Die `undefined` konstant ist ein Mitglied der `Global` Objekt und wird verfügbar, wenn das Skriptmodul initialisiert wird. Wenn eine Variable deklariert, aber nicht initialisiert wurde, wird sein Wert **undefined**.  
  
 Wenn eine Variable nicht deklariert wurde, können nicht verglichen werden es `undefined`, aber Sie können den Typ der Variablen, die die Zeichenfolge "undefined" vergleichen.  
  
 Die `undefined` konstant ist nützlich, wenn explizit Test- oder Festlegen der einer Variablen auf nicht definiert.  
  
## <a name="example"></a>Beispiel  
 Das folgende Beispiel zeigt, wie Sie die `undefined` konstant.  
  
```JavaScript  
// A variable that has not been initialized.  
var declared;  
  
if (declared == undefined)  
    document.write("declared has not been given a value <br/>");  
else  
    document.write("declared has been given a value <br/>");  
  
document.write("typeof declared is " + typeof(declared) + "<br/>");  
  
// An undeclared variable cannot be compared to undefined,  
// so the next line would generate an error.  
// if (notDeclared == undefined);  
  
document.write("typeof notDeclared is " + typeof(notDeclared));  
  
// Output:  
// declared has not been given a value  
// typeof declared is undefined  
// typeof notDeclared is undefined  
```  
  
## <a name="requirements"></a>Anforderungen  
 Die `undefined` Eigenschaft wurde in eingeführt [!INCLUDE[jsv55text](../../javascript/reference/includes/jsv55text-md.md)], und wurde versucht, schreibgeschützte in [!INCLUDE[jsv9textspecific](../../javascript/reference/includes/jsv9textspecific-md.md)].  
  
 **Gilt für**: [Global-Objekt](../../javascript/reference/global-object-javascript.md)  
  
## <a name="see-also"></a>Siehe auch  
 [typeof-Operator](../../javascript/reference/typeof-operator-decrementjavascript.md)