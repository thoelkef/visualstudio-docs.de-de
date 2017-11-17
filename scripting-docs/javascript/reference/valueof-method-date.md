---
title: ValueOf-Methode (Datum) | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 39a1f96e-14b0-4db2-b53d-cdfd67cbb208
caps.latest.revision: "3"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 87c5e6ea3c3e28d866f7cabf92dc97b81703b5b1
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="valueof-method-date"></a>valueOf-Methode (Datum)
Gibt die gespeicherte Zeit-Wert in Millisekunden seit Mitternacht des 1. Januar 1970 UTC zurück.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
date.valueOf()  
```  
  
#### <a name="parameters"></a>Parameter  
 Die `date` Objekt ist Instanz eines Datums.  
  
## <a name="return-value"></a>Rückgabewert  
 Die gespeicherte Zeit-Wert in Millisekunden seit Mitternacht des 1. Januar 1970 UTC. Dies ist der gleiche Wert wie `getTime`.  
  
## <a name="example"></a>Beispiel  
 Das folgende Beispiel veranschaulicht die Verwendung der `valueOf` Methode mit einem Datum.  
  
```JavaScript  
var myDate = new Date();  
myDate.setFullYear(2100, 5, 5);  
if (myDate.getTime() == myDate.valueOf())  
    document.write("values are the same");  
else  
    document.write("values are different");  
  
// Output: values are the same  
  
```  
  
## <a name="requirements"></a>Anforderungen  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]