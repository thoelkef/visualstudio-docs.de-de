---
title: IDiaPropertyStorage::ReadULONGLONG | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaPropertyStorage::ReadULONGLONG
ms.assetid: f80a2e24-5744-4fec-bab0-3ed51aef6e58
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5dea61b14cdee1ac260e4a21db0056abbdcad74f
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 01/25/2019
ms.locfileid: "54977381"
---
# <a name="idiapropertystoragereadulonglong"></a>IDiaPropertyStorage::ReadULONGLONG
Liest `ULONGLONG` Werte in einem Eigenschaftensatz.  
  
## <a name="syntax"></a>Syntax  
  
```C++  
HRESULT ReadULONGLONG (   
   PROPID     id,  
   ULONGLONG* pValue  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `id`  
 [in] Bezeichner für die Eigenschaft gelesen werden (`PROPID` ist in WTypes.h als definiert eine `ULONG`).  
  
 `pValue`  
 [out] Gibt den Wert der Eigenschaft zurück.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird `S_OK`; gibt andernfalls einen Fehlercode zurück. Gibt `E_INVALIDARG` ist die Eigenschaft nicht vom Typ `ULONGLONG`.  
  
## <a name="remarks"></a>Hinweise  
 Ein `ULONGLONG` wird von Windows als eine 64-Bit-Ganzzahl ohne Vorzeichen definiert.  
  
## <a name="see-also"></a>Siehe auch  
 [IDiaPropertyStorage](../../debugger/debug-interface-access/idiapropertystorage.md)