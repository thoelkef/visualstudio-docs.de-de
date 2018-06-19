---
title: GetUTCHours-Methode (Datum) (JavaScript) | Microsoft Docs
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
- getUTCHours
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- hours
- UTC times, returning
- getUTCHours method
ms.assetid: 7c9825dd-4b3a-4614-8e09-f40df123b630
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c47fe66e6eecb9e3aaa53f0d0988631062676d17
ms.sourcegitcommit: ba29e4d37db92ec784d4acf9c6e120cf0ea677e9
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/01/2018
ms.locfileid: "28943848"
---
# <a name="getutchours-method-date-javascript"></a>getUTCHours-Methode (Datum) (JavaScript)
Ruft den Wert der Stunden einer `Date` -Objekt unter Verwendung der koordinierten Weltzeit (UTC).  
  
## <a name="syntax"></a>Syntax  
  
```  
  
dateObj.getUTCHours()   
```  
  
#### <a name="parameters"></a>Parameter  
 Der erforderliche `dateObj` -Verweis ist ein `Date` -Objekt.  
  
## <a name="return-value"></a>Rückgabewert  
 Gibt eine ganze Zahl zwischen 0 und 23, der angibt, der Anzahl der seit Mitternacht vergangenen Stunden zurück. 0 (null) wird zurückgegeben, wenn die Uhrzeit früher als 1:00:00 Uhr ist. Wenn ein `Date` Objekt wurde erstellt, ohne dabei den Zeitpunkt, die Stunde ist standardmäßig 0 in UTC-Zeit. Diese Zeit ist möglicherweise nicht 0 (null) in anderen Zeitzonen.  
  
## <a name="remarks"></a>Hinweise  
 Beim Abrufen der Anzahl der seit Mitternacht vergangenen Stunden unter Verwendung der Ortszeit, verwenden Sie die `getHours` Methode.  
  
## <a name="example"></a>Beispiel  
 Im folgenden Beispiel wird die Verwendung der `getUTCHours`-Methode veranschaulicht.  
  
```JavaScript  
var date = new Date("1/1/2001");  
document.write(date.getUTCHours());  
document.write("<br/>");  
  
var date2 = new Date("1/1/2001 11:22:33");  
document.write(date2.getUTCHours());  
  
// Output (in the PST time zone):  
// 15 
// 2  
```  
  
## <a name="requirements"></a>Anforderungen  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **Gilt für**: [Date Object](../../javascript/reference/date-object-javascript.md)  
  
## <a name="see-also"></a>Siehe auch  
 [GetHours-Methode (Datum)](../../javascript/reference/gethours-method-date-javascript.md)   
 [SetHours-Methode (Datum)](../../javascript/reference/sethours-method-date-javascript.md)   
 [setUTCHours-Methode (Datum)](../../javascript/reference/setutchours-method-date-javascript.md)
