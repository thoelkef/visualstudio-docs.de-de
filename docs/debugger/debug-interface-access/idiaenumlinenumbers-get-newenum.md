---
title: 'IDiaEnumLineNumbers:: get__NewEnum | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumLineNumbers::get__NewEnum method
ms.assetid: 8b15f76b-a431-4f60-8bed-3206256b0d10
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 29126da6f11d6206b7eb7c92df83350b3094edff
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/22/2019
ms.locfileid: "72744415"
---
# <a name="idiaenumlinenumbersget__newenum"></a>IDiaEnumLineNumbers::get__NewEnum
Ruft die <xref:System.Runtime.InteropServices.ComTypes.IEnumVARIANT> Version dieses Enumerators ab.

## <a name="syntax"></a>Syntax

```C++
HRESULT get__NewEnum ( 
   IUnknown** pRetVal
);
```

#### <a name="parameters"></a>Parameter
 pRetVal

vorgenommen Gibt die `IUnknown`-Schnittstelle zurück, die die <xref:System.Runtime.InteropServices.ComTypes.IEnumVARIANT> Version dieses Enumerators darstellt.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird `S_OK` zurückgegeben. Andernfalls wird ein Fehlercode zurückgegeben.

## <a name="see-also"></a>Siehe auch
- [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md)