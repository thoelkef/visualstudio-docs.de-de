---
title: 'Idiapropertystorage:: locker | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaPropertyStorage::ReadULONGLONG
ms.assetid: f80a2e24-5744-4fec-bab0-3ed51aef6e58
caps.latest.revision: 12
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 6da509e226a612e80a10ca0759b5e264f31a1e13
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "62538680"
---
# <a name="idiapropertystoragereadulonglong"></a>IDiaPropertyStorage::ReadULONGLONG
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Liest `ULONGLONG` Werte in einem Eigenschaften Satz.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
HRESULT ReadULONGLONG (   
   PROPID     id,  
   ULONGLONG* pValue  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `id`  
 in Der Bezeichner der zu lesenden Eigenschaft ( `PROPID` ist in Wtypes. h als definiert `ULONG` ).  
  
 `pValue`  
 vorgenommen Gibt den Eigenschafts Wert zurück.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird zurückgegeben `S_OK` ; andernfalls wird ein Fehlercode zurückgegeben. Gibt zurück, `E_INVALIDARG` Wenn die Eigenschaft nicht vom Typ ist `ULONGLONG` .  
  
## <a name="remarks"></a>Bemerkungen  
 Eine `ULONGLONG` wird von Windows als eine 64-Bit-Ganzzahl ohne Vorzeichen definiert.  
  
## <a name="see-also"></a>Weitere Informationen  
 [IDiaPropertyStorage](../../debugger/debug-interface-access/idiapropertystorage.md)
