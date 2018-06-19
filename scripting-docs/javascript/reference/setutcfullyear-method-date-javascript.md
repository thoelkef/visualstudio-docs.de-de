---
title: SetUTCFullYear-Methode (Datum) (JavaScript) | Microsoft Docs
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
- setUTCFullYear
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- dates, UTC
- setUTCFullYear method
- UTC dates, setting
ms.assetid: e6c51b49-0149-4f9a-aa74-c73c0306f98e
caps.latest.revision: 13
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2dda8b75dd8bc8dac87ea383546f392b064c1d63
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
ms.locfileid: "24640990"
---
# <a name="setutcfullyear-method-date-javascript"></a>setUTCFullYear-Methode (Datum) (JavaScript)
Legt den Wert des Jahres den `Date` -Objekt unter Verwendung der koordinierten Weltzeit (UTC).  
  
## <a name="syntax"></a>Syntax  
  
```  
  
dateObj.setUTCFullYear(numYear[, numMonth[, numDate]])   
```  
  
## <a name="parameters"></a>Parameter  
 `dateObj`  
 Erforderlich. Ein `Date`-Objekt.  
  
 `numYear`  
 Erforderlich. Ein numerischer Wert, der das Jahr gleich ist.  
  
 `numMonth`  
 Dies ist optional. Ein numerischer Wert, der den Monat gleich ist. Der Wert für Januar ist 0 und andere Monatswerte hintereinander folgen. Muss angegeben werden, wenn *NumDate* angegeben wird.  
  
 *numDate*  
 Dies ist optional. Ein numerischer Wert, der den Tag des Monats gleich ist.  
  
## <a name="remarks"></a>Hinweise  
 Alle **festgelegt** Methoden, die optionale Argumente verwenden, den Rückgabewert aus entsprechenden **abrufen** Methoden, wenn Sie ein optionales Argument nicht angeben. Z. B. wenn die `numMonth` Argument nicht angegeben wird, [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] verwendet den Rückgabewert aus dem `getUTCMonth` Methode.  
  
 Darüber hinaus, wenn der Wert eines Arguments größer ist, dessen Bereich bzw. eine negative Zahl, andere gespeicherte Werte entsprechend geändert wird.  
  
 Verwenden Sie zum Festlegen des Jahres unter Verwendung der Ortszeit die `setFullYear` Methode.  
  
 Der Bereich von Jahren, die in unterstützt die `Date` Objekt beträgt etwa 285.616 Jahre von beiden Seiten des 1970.  
  
## <a name="example"></a>Beispiel  
 Im folgenden Beispiel wird die Verwendung der `setUTCFullYear`-Methode veranschaulicht.  
  
```JavaScript  
var dtFirst = new Date();  
dtFirst.setUTCFullYear(2007);  
  
var dtSecond = new Date();  
// 10 is the value for November.   
dtSecond.setUTCFullYear(2008, 10, 3);   
  
document.write (dtFirst.toUTCString());  
document.write ("<br />");  
document.write (dtSecond.toUTCString());  
```  
  
## <a name="requirements"></a>Anforderungen  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **Gilt für**: [Date Object](../../javascript/reference/date-object-javascript.md)  
  
## <a name="see-also"></a>Siehe auch  
 [GetFullYear-Methode (Datum)](../../javascript/reference/getfullyear-method-date-javascript.md)   
 [GetUTCFullYear-Methode (Datum)](../../javascript/reference/getutcfullyear-method-date-javascript.md)   
 [setFullYear-Methode (Datum)](../../javascript/reference/setfullyear-method-date-javascript.md)