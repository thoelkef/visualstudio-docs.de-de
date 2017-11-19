---
title: Caller-Eigenschaft (Funktion) (JavaScript) | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: caller
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- caller property
- function calls, functions that are executing
ms.assetid: ae210853-7160-4102-9cfd-ab489f180ce1
caps.latest.revision: "12"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8c6eef1b8304612c2ed16a4cc389bf3b2a28b70f
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="caller-property-function-javascript"></a>caller-Eigenschaft (Funktion) (JavaScript)
Ruft die Funktion, die die aktuelle Funktion aufgerufen hat.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
functionName.caller  
```  
  
## <a name="remarks"></a>Hinweise  
 Die `functionName` -Objekt der Namen der Funktion ausgeführt.  
  
 Die `caller` Eigenschaft für eine Funktion nur bei definiert, die Funktion ausgeführt wird. Wenn die Funktion von der obersten Position der aufgerufen wird eine [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] -Programm `caller` enthält `null`.  
  
 Wenn die `caller` Eigenschaft in einer Zeichenfolge verwendet wird, das Ergebnis entspricht dem `functionName`.`toString`, d. h. die dekompilierte Text der Funktion angezeigt wird.  
  
 Das folgende Beispiel veranschaulicht die Verwendung der `caller`-Eigenschaft.  
  
```JavaScript  
function CallLevel(){  
   if (CallLevel.caller == null)  
      return("CallLevel was called from the top level.");  
   else  
      return("CallLevel was called by another function.");  
}  
  
document.write(CallLevel());  
  
// Output: CallLevel was called from the top level.  
```  
  
## <a name="requirements"></a>Anforderungen  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]  
  
## <a name="see-also"></a>Siehe auch  
 [function-Anweisung](../../javascript/reference/function-statement-javascript.md)