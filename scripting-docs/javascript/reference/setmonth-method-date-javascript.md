---
title: SetMonth-Methode (Datum) (JavaScript) | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: setMonth
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- Month method
- setMonth method
ms.assetid: 4f5be295-d536-46c0-b3a4-ad06457efe82
caps.latest.revision: "15"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0f2672abebd327af8b0da58d46ebc183b8159711
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="setmonth-method-date-javascript"></a>setMonth-Methode (Datum) (JavaScript)
Legt den Monatswert fest, dem `Date` -Objekt unter Verwendung der Ortszeit.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
dateObj. setMonth(numMonth[, dateVal])   
```  
  
## <a name="parameters"></a>Parameter  
 `dateObj`  
 Erforderlich. Ein `Date`-Objekt.  
  
 `numMonth`  
 Erforderlich. Ein numerischer Wert, der den Monat gleich ist. Der Wert für Januar ist 0 und andere Monatswerte hintereinander folgen.  
  
 `dateVal`  
 Dies ist optional. Ein numerischer Wert, der den Tag des Monats darstellt. Wenn dieser Wert nicht angegeben ist, den Wert von einem Aufruf der `getDate` Methode verwendet wird.  
  
## <a name="remarks"></a>Hinweise  
 Um den Monatswert unter Verwendung der koordinierten Weltzeit (UTC) festzulegen, verwenden Sie die `setUTCMonth` Methode.  
  
 Wenn der Wert des `numMonth` ist größer als 11 (Januar ist Monat 0) bzw. eine negative Zahl, die gespeicherte Jahr entsprechend geändert. Wenn das gespeicherte Datum "5. Januar 1996" ist beispielsweise und **setMonth(14)** wird aufgerufen, das Datum wird geändert in "5. März 1997".  
  
 Die **SetFullYear** Methode kann verwendet werden, um das Jahr, Monat und Tag des Monats festgelegt.  
  
## <a name="example"></a>Beispiel  
 Im folgenden Beispiel wird die Verwendung der `setMonth`-Methode veranschaulicht.  
  
```JavaScript  
date = new Date('1/1/1990');  
date.setMonth(14);  
document.write(date);  
  
// Output: Fri Mar 1 00:00:00 PST 1991  
// Note that the time zone corresponds to the time zone on the local computer.  
  
```  
  
## <a name="requirements"></a>Anforderungen  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **Gilt für**: [Date Object](../../javascript/reference/date-object-javascript.md)  
  
## <a name="see-also"></a>Siehe auch  
 [GetMonth-Methode (Datum)](../../javascript/reference/getmonth-method-date-javascript.md)   
 [GetUTCMonth-Methode (Datum)](../../javascript/reference/getutcmonth-method-date-javascript.md)   
 [setUTCMonth-Methode (Datum)](../../javascript/reference/setutcmonth-method-date-javascript.md)