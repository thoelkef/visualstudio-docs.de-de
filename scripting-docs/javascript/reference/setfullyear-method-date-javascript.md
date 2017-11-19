---
title: SetFullYear-Methode (Datum) (JavaScript) | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: setFullYear
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- Year method
- setFullYear method
- dates, setting
ms.assetid: 635e4f5a-0210-4c01-8152-b0da4146f6ff
caps.latest.revision: "16"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1e5e20a8486d1aefeab9b244c5f1e9d1b1e60c3f
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="setfullyear-method-date-javascript"></a>setFullYear-Methode (Datum) (JavaScript)
Das Jahr des legt die `Date` -Objekt unter Verwendung der Ortszeit.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
dateObj.setFullYear(numYear[, numMonth[, numDate]])   
```  
  
## <a name="parameters"></a>Parameter  
 `dateObj`  
 Erforderlich. Ein `Date`-Objekt.  
  
 `numYear`  
 Erforderlich. Ein numerischer Wert für das Jahr.  
  
 `numMonth`  
 Dies ist optional. Ein nullbasierter numerischen Wert für den Monat (0 für den 11. Januar für Dezember). Muss angegeben werden, wenn `numDate` angegeben ist.  
  
 `numDate`  
 Dies ist optional. Ein numerischer Wert, der für den Tag des Monats gleich ist.  
  
## <a name="remarks"></a>Hinweise  
 Alle **festgelegt** Methoden, die optionale Argumente verwenden, den Rückgabewert aus entsprechenden **abrufen** Methoden, wenn Sie das optionale Argument nicht angeben. Z. B. wenn die `numMonth` Argument ist optional, aber nicht angegeben, [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] verwendet den Rückgabewert aus dem **GetMonth** Methode.  
  
 Darüber hinaus wird das Datum ist der Wert eines Arguments größer als dessen Bereich Kalender bzw. negativ, vorwärts oder rückwärts nach Bedarf.  
  
 Um das Jahr mit Universal Coordinated Time (UTC) festzulegen, verwenden die `setUTCFullYear` Methode.  
  
 Der Bereich von Jahren, die in der Date-Objekt unterstützt beträgt etwa 285.616 Jahre vor und nach 1970.  
  
## <a name="example"></a>Beispiel  
 Das folgende Beispiel veranschaulicht die Verwendung der `setFullYear` Methode:  
  
```JavaScript  
var date1 = new Date("1/1/2001");  
date1.setFullYear(2007);  
  
var date2 = new Date("1/1/2001");  
date2.setFullYear(2008, 10, 3);   
  
document.write (date1.toLocaleString());  
document.write ("<br />");  
document.write (date2.toLocaleString());  
  
// Output:  
// Monday, January 01, 2007 12:00:00 AM  
// Monday, November 03, 2008 12:00:00 AM  
```  
  
## <a name="requirements"></a>Anforderungen  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **Gilt für**: [Date Object](../../javascript/reference/date-object-javascript.md)  
  
## <a name="see-also"></a>Siehe auch  
 [GetFullYear-Methode (Datum)](../../javascript/reference/getfullyear-method-date-javascript.md)   
 [GetUTCFullYear-Methode (Datum)](../../javascript/reference/getutcfullyear-method-date-javascript.md)   
 [setUTCFullYear-Methode (Datum)](../../javascript/reference/setutcfullyear-method-date-javascript.md)