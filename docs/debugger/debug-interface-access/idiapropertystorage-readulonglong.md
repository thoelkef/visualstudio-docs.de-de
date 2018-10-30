---
title: IDiaPropertyStorage::ReadULONGLONG | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaPropertyStorage::ReadULONGLONG
ms.assetid: f80a2e24-5744-4fec-bab0-3ed51aef6e58
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 457ca1d493498e0592c572ae0c93d7d2d6a01d30
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49867649"
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