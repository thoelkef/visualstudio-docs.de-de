---
title: SetMinutes-Methode (Datum) (JavaScript) | Microsoft Docs
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
- setMinutes
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- minutes
- setMinutes method
ms.assetid: 34c959cd-cd29-4cee-8e04-9061cf6d42f3
caps.latest.revision: 13
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1ce40cb3ebf769cdd8f668e246e272833780434d
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
ms.locfileid: "24641190"
---
# <a name="setminutes-method-date-javascript"></a>setMinutes-Methode (Datum) (JavaScript)
Legt den Minutenwert der **Datum** -Objekt unter Verwendung der Ortszeit.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
dateObj.setMinutes(numMinutes[, numSeconds[, numMilli]])   
```  
  
## <a name="parameters"></a>Parameter  
 `dateObj`  
 Erforderlich. Ein `Date`-Objekt.  
  
 `numMinutes`  
 Erforderlich. Ein numerischer Wert, der gleich dem Minutenwert ist. Muss angegeben werden, wenn eines der folgenden Argumente verwendet wird.  
  
 *numSeconds*  
 Dies ist optional. Ein numerischer Wert gleich dem Sekundenwert. Muss angegeben werden, wenn die `numMilli` Argument verwendet wird.  
  
 `numMilli`  
 Dies ist optional. Ein numerischer Wert, der gleich dem Millisekundenwert ist.  
  
## <a name="remarks"></a>Hinweise  
 Alle **festgelegt** Methoden, die optionale Argumente verwenden, den Rückgabewert aus entsprechenden **abrufen** Methoden, wenn Sie ein optionales Argument nicht angeben. Z. B. wenn die *NumSeconds* Argument nicht angegeben wird, [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] verwendet den Rückgabewert aus dem `getSeconds` Methode.  
  
 Um den Minutenwert unter Verwendung der koordinierten Weltzeit (UTC) festzulegen, verwenden Sie die `setUTCMinutes` Methode.  
  
 Ist der Wert eines Arguments größer als dessen Bereich bzw. eine negative Zahl, werden andere gespeicherte Werte entsprechend geändert. Wenn das gespeicherte Datum z. B. "5. Januar 1996 00:00:00" und **setMinutes(90)** ist aufgerufen wird, wird das Datum in geändert "5. Januar 1996 01:30:00." Negative Zahlen haben ein ähnliches Verhalten.  
  
## <a name="example"></a>Beispiel  
 Im folgenden Beispiel wird die Verwendung der `setMinutes`-Methode veranschaulicht.  
  
```JavaScript  
function SetMinutesDemo(nmin, nsec){  
   var d, s;                     // Declare variables.  
   d = new Date();               // Create Date object.  
   d.setMinutes(nmin, nsec);     // Set minutes.  
   s = "Current setting is " + d.toLocaleString()   
   return(s);                    // Return new setting.  
}  
```  
  
## <a name="requirements"></a>Anforderungen  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **Gilt für**: [Date Object](../../javascript/reference/date-object-javascript.md)  
  
## <a name="see-also"></a>Siehe auch  
 [GetMinutes-Methode (Datum)](../../javascript/reference/getminutes-method-date-javascript.md)   
 [GetUTCMinutes-Methode (Datum)](../../javascript/reference/getutcminutes-method-date-javascript.md)   
 [setUTCMinutes-Methode (Datum)](../../javascript/reference/setutcminutes-method-date-javascript.md)