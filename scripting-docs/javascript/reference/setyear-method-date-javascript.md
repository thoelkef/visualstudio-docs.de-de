---
title: SetYear-Methode (Datum) (JavaScript) | Microsoft Docs
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
- setYear
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- Year method
- setYear method
ms.assetid: 36431050-e0ec-45ee-830d-0d7c20e207ea
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5a9318de4a9420e0518dcd7f00a51c7161a8f92c
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="setyear-method-date-javascript"></a>setYear-Methode (Datum) (JavaScript)
Legt den Wert des Jahres den `Date` Objekt.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
dateObj.setYear(numYear)   
```  
  
## <a name="parameters"></a>Parameter  
 `dateObj`  
 Erforderlich. Ein `Date`-Objekt.  
  
 `numYear`  
 Erforderlich. Für den Jahren 1900 bis 1999 ist dies ein numerischer Wert, der gleich dem Jahr minus 1900. Für die Datumsangaben außerhalb dieses Bereichs liegt ist dies einen numerischen Wert mit 4.  
  
## <a name="remarks"></a>Hinweise  
 Diese Methode ist veraltet und wird nur für die Abwärtskompatibilität beibehalten. Verwenden Sie stattdessen die `setFullYear`-Methode.  
  
 Das Jahr des Festlegen einer `Date` Objekt 1997 Aufruf **setYear(97)**. Rufen Sie zum Festlegen der Jahr 2010 **setYear(2010)**. Um das Jahr bis zu einem Jahr im Bereich von 0 bis 99 festzulegen, verwenden Sie abschließend die `setFullYear` Methode.  
  
> [!NOTE]
>  Für [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] Version 1.0, `setYear` verwendet einen Wert, der das Ergebnis der Addition von 1900 und den Wert des Jahres gebotenen ist `numYear`, unabhängig vom Wert des Jahres. Um beispielsweise das Jahr 1899 festlegen `numYear` ist-1 und das Jahr 2000 festlegen `numYear` ist 100.  
  
## <a name="requirements"></a>Anforderungen  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **Gilt für**: [Date Object](../../javascript/reference/date-object-javascript.md)  
  
## <a name="see-also"></a>Siehe auch  
 [GetFullYear-Methode (Datum)](../../javascript/reference/getfullyear-method-date-javascript.md)   
 [GetUTCFullYear-Methode (Datum)](../../javascript/reference/getutcfullyear-method-date-javascript.md)   
 [GetYear-Methode (Datum)](../../javascript/reference/getyear-method-date-javascript.md)   
 [SetFullYear-Methode (Datum)](../../javascript/reference/setfullyear-method-date-javascript.md)   
 [setUTCFullYear-Methode (Datum)](../../javascript/reference/setutcfullyear-method-date-javascript.md)