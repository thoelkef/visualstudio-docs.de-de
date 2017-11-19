---
title: IDiaPropertyStorage::ReadDWORD | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: IDiaPropertyStorage::ReadDWORD
ms.assetid: 5f4c034e-a9d3-4560-94b5-ede524741439
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 178eb0cceaacd6d93f20e74c034e452d8f7fdf6f
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="idiapropertystoragereaddword"></a>IDiaPropertyStorage::ReadDWORD
Liest `DWORD` Werte in einem Eigenschaftensatz.  
  
## <a name="syntax"></a>Syntax  
  
```C++  
HRESULT ReadDWORD (   
   PROPID id,  
   DWORD* pValue  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `id`  
 [in] Bezeichner für die Eigenschaft gelesen werden (`PROPID` ist definiert in WTypes.h als eine `ULONG`).  
  
 `pValue`  
 [out] Gibt den Wert der Eigenschaft zurück.  
  
## <a name="return-value"></a>Rückgabewert  
 Im Erfolgsfall gibt `S_OK`; andernfalls wird ein Fehlercode zurückgegeben. Gibt `E_INVALIDARG` Wenn die Eigenschaft nicht vom Typ `DWORD`.  
  
## <a name="remarks"></a>Hinweise  
 Ein `DWORD` wird von Windows als 32-Bit-Ganzzahl ohne Vorzeichen definiert.  
  
## <a name="see-also"></a>Siehe auch  
 [IDiaPropertyStorage](../../debugger/debug-interface-access/idiapropertystorage.md)