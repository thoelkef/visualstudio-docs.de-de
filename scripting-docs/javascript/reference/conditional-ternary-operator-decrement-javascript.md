---
title: "Bedingter (ternärer) Operator (?:)) (JavaScript) | Microsoft Docs"
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
- '?:'
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- conditional operators
- conditional (Ternary) operator
- ternary
ms.assetid: 7399ac32-9324-4a9a-ae76-be9c0f9df81c
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1dc34b5c633cfc02219cb01061e1aaa017e0f7f2
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="conditional-ternary-operator--javascript"></a>Bedingter (ternärer) Operator (?:) (JavaScript)
Gibt in Abhängigkeit von einer Bedingung einen der zwei Ausdrücke zurück.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
test ? expression1 : expression2  
```  
  
## <a name="parameters"></a>Parameter  
 `test`  
 Beliebiger boolescher Ausdruck.  
  
 `expression1`  
 Ein zurückgegebener Ausdruck, wenn `test` den Wert `true` hat. Kann ein Kommaausdruck sein.  
  
 `expression2`  
 Ein zurückgegebener Ausdruck, wenn `test` den Wert `false` hat. Durch einen Kommaausdruck können mehrere Ausdrücke verknüpft sein.  
  
## <a name="remarks"></a>Hinweise  
 Der `?:`-Operator kann als Kurzform für eine `if...else`-Anweisung verwendet werden. Er wird in der Regel als Teil eines umfangreicheren Ausdrucks verwendet, der durch eine `if...else`-Anweisung noch komplexer werden würde. Zum Beispiel:  
  
```JavaScript  
var now = new Date();  
var greeting = "Good" + ((now.getHours() > 17) ? " evening." : " day.");  
```  
  
 Das Beispiel erstellt eine Zeichenfolge mit "Guten Abend." Wenn der 18.00 Uhr ist. Der entsprechende Code mit einer `if...else`-Anweisung würde wie folgt aussehen:  
  
```JavaScript  
var now = new Date();  
var greeting = "Good";  
if (now.getHours() > 17)  
   greeting += " evening.";  
else  
   greeting += " day.";  
```  
  
## <a name="requirements"></a>Anforderungen  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>Siehe auch  
 [If... else-Anweisung](../../javascript/reference/if-dot-dot-dot-else-statement-javascript.md)   
 [Operatorrangfolge](../../javascript/operator-subtractprecedence-javascript.md)   
 [Zusammenfassung der Operatoren (JavaScript)](../../javascript/misc/operator-subtractsummary-javascript.md)   
 [Beispiel-app für Script Junkie Konfiguration widget](http://code.msdn.microsoft.com/Script-Junkie-Configuration-543ece24)