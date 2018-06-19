---
title: Debugger-Anweisung (JavaScript) | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- debugger_JavaScriptKeyword
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- debugger statement
ms.assetid: c6d2e193-c1f7-4fb3-8a4e-cc9823174ae4
caps.latest.revision: 17
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9e64e860cebd065f357857484e932b4aea3f05ea
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
ms.locfileid: "24636200"
---
# <a name="debugger-statement-javascript"></a>debugger-Anweisung (JavaScript)
Hält die Ausführung.  
  
## <a name="syntax"></a>Syntax  
  
```  
debugger  
```  
  
## <a name="remarks"></a>Hinweise  
 Sie können platzieren `debugger` -Anweisungen an einer beliebigen Stelle in Prozeduren Ausführung zu unterbrechen. Mithilfe der `debugger` -Anweisung entspricht dem Festlegen eines Haltepunkts im Code.  
  
 Die `debugger` Anweisung hält die Ausführung, aber schließen Sie alle Dateien oder keine Variablen löschen.  
  
> [!NOTE]
>  Die `debugger` Anweisung hat keine Auswirkungen, es sei denn, das Skript debuggt wird.  
  
## <a name="example"></a>Beispiel  
 Dieses Beispiel verwendet die `debugger` Anweisung Anhalten der Ausführung für jede Iteration durch die `for` Schleife.  
  
> [!NOTE]
>  Um dieses Beispiel auszuführen, benötigen Sie einen Skriptdebugger installiert, und das Skript muss im Debugmodus ausgeführt.  
>   
>  Internet Explorer 8 umfasst die [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] Debugger. Wenn Sie eine frühere Version von Internet Explorer verwenden, finden Sie unter [Gewusst wie: Aktivieren und Starten des Skriptdebuggings in Internet Explorer](http://go.microsoft.com/fwlink/?LinkId=133801)weitere Informationen.  
  
```JavaScript  
for(i = 1; i<5; i++) {  
   // Print i to the Output window.  
   Debug.write("loop index is " + i);  
   // Wait for user to resume.  
   debugger  
}  
```  
  
## <a name="requirements"></a>Anforderungen  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
## <a name="see-also"></a>Siehe auch  
 [JavaScript-Anweisungen](../../javascript/reference/javascript-statements.md)   
 [Bedingte Kompilierung](../../javascript/advanced/conditional-compilation-javascript.md)