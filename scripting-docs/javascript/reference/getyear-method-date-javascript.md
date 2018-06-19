---
title: GetYear-Methode (Datum) (JavaScript) | Microsoft Docs
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
- getYear
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- dates, returning year
- GetYear method
ms.assetid: 0e23e832-acd4-49a9-a175-515d0094f172
caps.latest.revision: 19
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a0e08fae8da1b102918de70650d09080a7ff7ebd
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
ms.locfileid: "24637080"
---
# <a name="getyear-method-date-javascript"></a>getYear-Methode (Datum) (JavaScript)
Ruft das Jahr des ein `Date` Objekt.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
dateObj.getYear()   
```  
  
#### <a name="parameters"></a>Parameter  
 Der erforderliche `dateObj` -Verweis ist ein `Date` -Objekt.  
  
## <a name="return-value"></a>Rückgabewert  
 Gibt das Jahr zurück.  
  
## <a name="remarks"></a>Hinweise  
  
> [!IMPORTANT]
>  Diese Methode ist veraltet und wird nur für Abwärtskompatibilität bereitgestellt. Verwenden Sie stattdessen die `getFullYear`-Methode.  
  
 In [!INCLUDE[jsv1textspecific](../../javascript/reference/includes/jsv1textspecific-md.md)], und klicken Sie dann in Internet Explorer-Versionen ab [!INCLUDE[jsv9textspecific](../../javascript/reference/includes/jsv9textspecific-md.md)], ist der zurückgegebene Wert dem gespeicherten Jahr minus 1900. Beispielsweise wird das Jahr 1899 als-1 zurückgegeben, und das Jahr 2000 als 100 zurückgegeben wird.  
  
 In [!INCLUDE[jsv3textspecific](../../javascript/reference/includes/jsv3textspecific-md.md)] über [!INCLUDE[jsv58textspecific](../../javascript/reference/includes/jsv58textspecific-md.md)], die Formel für das Jahr abhängig ist. Für den Jahren 1900 bis 1999 ist der zurückgegebene Wert ein 2-Ziffern-Wert, der das gespeicherte Jahr minus 1900 liegt. Datumsangaben außerhalb dieses Bereichs liegt wird das Jahr 4 Ziffern zurückgegeben. Beispielsweise 1996 als 96 zurückgegeben wird, aber 1825 und 2025 werden unverändert zurückgegeben.  
  
## <a name="requirements"></a>Anforderungen  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **Gilt für**: [Date Object](../../javascript/reference/date-object-javascript.md)  
  
## <a name="see-also"></a>Siehe auch  
 [GetFullYear-Methode (Datum)](../../javascript/reference/getfullyear-method-date-javascript.md)   
 [GetUTCFullYear-Methode (Datum)](../../javascript/reference/getutcfullyear-method-date-javascript.md)   
 [SetFullYear-Methode (Datum)](../../javascript/reference/setfullyear-method-date-javascript.md)   
 [SetUTCFullYear-Methode (Datum)](../../javascript/reference/setutcfullyear-method-date-javascript.md)   
 [setYear-Methode (Datum)](../../javascript/reference/setyear-method-date-javascript.md)