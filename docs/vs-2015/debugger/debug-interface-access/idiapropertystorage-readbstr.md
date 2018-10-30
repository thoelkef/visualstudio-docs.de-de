---
title: IDiaPropertyStorage::ReadBSTR | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- IDiaPropertyStorage::ReadBSTR
ms.assetid: 7214643b-3286-48ed-90aa-0fe95b4cae5b
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0363cbc8923303ba3ea5ce12a31e68d3bdf5d955
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49933000"
---
# <a name="idiapropertystoragereadbstr"></a>IDiaPropertyStorage::ReadBSTR
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Liest `BSTR` Werte in einem Eigenschaftensatz.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
HRESULT ReadBSTR (   
   PROPID id,  
   BSTR*  pValue  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `id`  
 [in] Bezeichner für die Eigenschaft gelesen werden (`PROPID` ist in WTypes.h als definiert eine `ULONG`).  
  
 `pValue`  
 [out] Gibt den Wert der Eigenschaft zurück.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird `S_OK`; gibt andernfalls einen Fehlercode zurück. Gibt `E_INVALIDARG` ist die Eigenschaft nicht vom Typ `BSTR`.  
  
## <a name="remarks"></a>Hinweise  
 Ein `BSTR` wird von Windows als 0 (null) endende Breite Zeichenfolge definiert.  
  
## <a name="see-also"></a>Siehe auch  
 [IDiaPropertyStorage](../../debugger/debug-interface-access/idiapropertystorage.md)



