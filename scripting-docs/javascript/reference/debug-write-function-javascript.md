---
title: Debug.Write-Funktion (JavaScript) | Microsoft Docs
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
- Write
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- write method [JavaScript]
ms.assetid: fd1cfbb3-46cb-47cc-896c-a70d457dd413
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 74aad7a01e0dc166f22173cf193b312e1fd4d804
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="debugwrite-function-javascript"></a>Debug.write-Funktion (JavaScript)
Zeichenfolgen an den Skriptdebugger gesendet.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
Debug.write([str1 [, str2 [, ... [, strN]]]])  
```  
  
## <a name="parameters"></a>Parameter  
 *str1, str2,..., strN*  
 Dies ist optional. Zeichenfolgen an den Skriptdebugger senden.  
  
## <a name="remarks"></a>Hinweise  
 Die `Debug.write` -Funktion sendet Zeichenfolgen an das Direktfenster ein Script-Debugger zur Laufzeit. Wenn das Skript nicht debuggt wird, die `Debug.write` Funktion hat keine Auswirkungen.  
  
 Die `Debug.write` Funktion ist fast identisch mit der `Debug.writeln` Funktion. Der einzige Unterschied besteht darin, die die `Debug.writeln` -Funktion sendet ein Zeilenumbruchzeichen, nachdem die Zeichenfolgen gesendet werden.  
  
## <a name="example"></a>Beispiel  
 Dieses Beispiel verwendet die `Debug.write` Funktion, um den Wert der Variablen im Script Debugger das "Direktfenster" anzuzeigen.  
  
> [!NOTE]
>  Um dieses Beispiel auszuführen, benötigen Sie einen Skriptdebugger installiert, und das Skript muss im Debugmodus ausgeführt.  
>   
>  Internet Explorer 8 umfasst die [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] Debugger. Wenn Sie eine frühere Version von Internet Explorer verwenden, finden Sie unter [Gewusst wie: Aktivieren und Starten des Skriptdebuggings in Internet Explorer](http://go.microsoft.com/fwlink/?LinkId=133801)weitere Informationen.  
  
```JavaScript  
var counter = 42;  
Debug.write("The value of counter is " + counter);  
```  
  
## <a name="requirements"></a>Anforderungen  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **Gilt für**: [Debug-Objekt](../../javascript/reference/debug-object-javascript.md)  
  
## <a name="see-also"></a>Siehe auch  
 [Debug.writeln-Funktion](../../javascript/reference/debug-writeln-function-javascript.md)