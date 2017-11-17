---
title: Debug.writeln-Funktion (JavaScript) | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: writeln
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords: writeIn method
ms.assetid: c3aad0cd-0486-4161-9ba6-31d672da72af
caps.latest.revision: "17"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 848760e59632b05605de2d73615a2b025df363da
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="debugwriteln-function-javascript"></a>Debug.writeln-Funktion (JavaScript)
Zeichenfolgen an den Skriptdebugger, gefolgt von einem Zeilenumbruchzeichen gesendet.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
Debug.writeln([str1 [, str2 [, ... [, strN]]]])  
```  
  
## <a name="parameters"></a>Parameter  
 *str1, str2,..., strN*  
 Dies ist optional. Zeichenfolgen an den Skriptdebugger senden.  
  
## <a name="remarks"></a>Hinweise  
 Die `Debug.writeln` -Funktion sendet die Zeichenfolgen, gefolgt von einem neue Zeilenumbruchzeichen, das "Direktfenster" Microsoft Script Debugger zur Laufzeit. Wenn das Skript nicht debuggt wird, die `Debug.writeln` Funktion hat keine Auswirkungen.  
  
 Die `Debug.writeln` Funktion ist fast identisch mit der `Debug.write` Funktion. Der einzige Unterschied besteht darin, die die `Debug.write` Funktion sendet kein neue Zeilenumbruchzeichen nach dem Senden von Zeichenfolgen.  
  
## <a name="example"></a>Beispiel  
 Dieses Beispiel verwendet die `Debug.writeln` Funktion, um den Wert der Variablen im Microsoft Script Debugger das "Direktfenster" anzuzeigen.  
  
> [!NOTE]
>  Um dieses Beispiel auszuführen, benötigen Sie einen Skriptdebugger installiert, und das Skript muss im Debugmodus ausgeführt.  
>   
>  Internet Explorer 8 umfasst die [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] Debugger. Wenn Sie eine frühere Version von Internet Explorer verwenden, finden Sie unter [Gewusst wie: Aktivieren und Starten des Skriptdebuggings in Internet Explorer](http://go.microsoft.com/fwlink/?LinkId=133801)weitere Informationen.  
  
```JavaScript  
var counter = 42;  
Debug.writeln("The value of counter is " + counter);  
```  
  
## <a name="requirements"></a>Anforderungen  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **Gilt für**: [Debug-Objekt](../../javascript/reference/debug-object-javascript.md)  
  
## <a name="see-also"></a>Siehe auch  
 [Debug.write-Funktion](../../javascript/reference/debug-write-function-javascript.md)