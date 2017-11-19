---
title: GetVarDate-Methode (Datum) (JavaScript) | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: getVarDate
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- Date object
- getVarDate method
- dates, VT_DATE format
ms.assetid: 561238de-5c91-45a3-b839-a16910d3a1cf
caps.latest.revision: "18"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d21394a5381653997a6b406537a6bde4f5266b97
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="getvardate-method-date-javascript"></a>getVarDate-Methode (Datum) (JavaScript)
Gibt einen VT_DATE-Wert von einem `Date` -Objekt zurück  
  
> [!WARNING]
>  Diese Methode wird nur in Internet Explorer unterstützt.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
dateObj.getVarDate()   
```  
  
#### <a name="parameters"></a>Parameter  
 Der erforderliche `dateObj` -Verweis ist ein `Date` -Objekt.  
  
## <a name="return-value"></a>Rückgabewert  
 Gibt einen VT_DATE-Wert zurück  
  
## <a name="remarks"></a>Hinweise  
 Die `getVarDate` -Methode wird verwendet, wenn JavaScript-Code mit COM-Objekten, ActiveX-Objekten oder anderen Objekten interagiert, die Datumswerte im VT_DATE-Format akzeptieren und zurückgegeben. Hierzu gehören Objekte in Visual Basic und Visual Basic Scripting Edition (VBScript). Das tatsächliche Format des zurückgegebenen Werts hängt von regionalen Einstellungen ab.  
  
## <a name="requirements"></a>Anforderungen  
 Wird in den folgenden Dokumentmodi unterstützt: Quirksmodus, Internet Explorer 6-Standardmodus, Internet Explorer 7-Standardmodus, Internet Explorer 8-Standardmodus, Internet Explorer 9-Standardmodus und Internet Explorer 10-Standardmodus. Wird in [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)] -Apps nicht unterstützt. Siehe [Versionsinformationen](../../javascript/reference/javascript-version-information.md).  
  
 **Gilt für**: [Date Object](../../javascript/reference/date-object-javascript.md)  
  
## <a name="see-also"></a>Siehe auch  
 [GetDate-Methode (Datum)](../../javascript/reference/getdate-method-date-javascript.md)   
 [Date.parse-Funktion](../../javascript/reference/date-parse-function-javascript.md)