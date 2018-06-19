---
title: ToGMTString-Methode (Datum) (JavaScript) | Microsoft Docs
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
- toGMTString
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- toGMTString method
ms.assetid: 9dc1e722-5722-4b8c-a213-a2650f55f207
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: cef8a61e04fbb5ada6e03fa946f434327422d9d7
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
ms.locfileid: "24640110"
---
# <a name="togmtstring-method-date-javascript"></a>toGMTString-Methode (Datum) (JavaScript)
Gibt ein Datum mit Greenwich bedeuten Time(GMT) in eine Zeichenfolge konvertiert.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
dateObj.toGMTString()   
```  
  
## <a name="remarks"></a>Hinweise  
 Die erforderliche `dateObj` Verweis ist "any" `Date` Objekt.  
  
 Die `toGMTString` Methode ist veraltet und wird nur für die Abwärtskompatibilität bereitgestellt. Es wird empfohlen, Sie verwenden die `toUTCString` Methode stattdessen.  
  
 Die `toGMTString` Methode gibt ein `String` -Objekt, das Datum enthält, formatiert GMT-Konvention. Das Format des Rückgabewerts ist wie folgt: "05 Jan 1996 00:00:00 Uhr GMT".  
  
## <a name="requirements"></a>Anforderungen  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **Gilt für**: [Date Object](../../javascript/reference/date-object-javascript.md)  
  
## <a name="see-also"></a>Siehe auch  
 [toUTCString-Methode (Datum)](../../javascript/reference/toutcstring-method-date-javascript.md)