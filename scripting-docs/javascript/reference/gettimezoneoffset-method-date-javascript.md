---
title: GetTimezoneOffset-Methode (Datum) (JavaScript) | Microsoft Docs
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
- getTimeZoneOffset
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- getTimezoneOffset method
- time zones [Visual Studio]
ms.assetid: 58ee22b0-4688-45bd-a337-cc23119b09ce
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e49a3c8b7060e6097300f8aaf99b2ef869833018
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="gettimezoneoffset-method-date-javascript"></a>getTimezoneOffset-Methode (Datum) (JavaScript)
Ruft den Unterschied zwischen der Zeit auf dem lokalen Computer und Universal Coordinated Time (UTC) in Minuten ab.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
dateObj.getTimezoneOffset()   
```  
  
#### <a name="parameters"></a>Parameter  
 Der erforderliche `dateObj` -Verweis ist ein `Date` -Objekt.  
  
## <a name="return-value"></a>Rückgabewert  
 Gibt die Anzahl der Minuten zwischen dem Zeitpunkt auf dem aktuellen Computer (entweder auf den Clientcomputer oder, wenn diese Methode, von einem Serverskript den Servercomputer aufgerufen wird) und UTC. Es ist positive des Computers, auf die aktuelle lokale Zeit hinter UTC (z. B. Pacific Daylight Time) und Negative ist die lokale Zeit des Computers vor UTC (z. B. Japan). Wenn die Verbindung mit ein Server in New York City am 1. Dezember durch einen Client in Los Angeles `getTimezoneOffset` gibt 480 zurück, wenn auf dem Client oder 300 ausgeführt werden soll, wenn auf dem Server ausgeführt.  
  
## <a name="remarks"></a>Hinweise  
  
## <a name="example"></a>Beispiel  
 Im folgenden Beispiel wird die Verwendung der `getTimezoneOffset`-Methode gezeigt.  
  
```JavaScript  
var date =  new Date();  
var minutes = date.getTimezoneOffset();  
  
if (minutes < 0)  
    document.write(minutes / 60 + " hours after UTC");  
else  
    document.write(minutes / 60 + " hours before UTC");  
  
// Output (for example, where local time is PST):   
7 hours before UTC  
  
```  
  
## <a name="requirements"></a>Anforderungen  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **Gilt für**: [Date Object](../../javascript/reference/date-object-javascript.md)  
  
## <a name="see-also"></a>Siehe auch  
 [getTime-Methode (Datum)](../../javascript/reference/gettime-method-date-javascript.md)