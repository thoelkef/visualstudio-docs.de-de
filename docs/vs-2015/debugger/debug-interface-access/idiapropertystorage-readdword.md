---
title: 'Idiapropertystorage:: Read-Word | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaPropertyStorage::ReadDWORD
ms.assetid: 5f4c034e-a9d3-4560-94b5-ede524741439
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: e92b74fc1165adf359614e354ab60f3fc118e34b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "62538838"
---
# <a name="idiapropertystoragereaddword"></a>IDiaPropertyStorage::ReadDWORD
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Liest `DWORD` Werte in einem Eigenschaften Satz.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
HRESULT ReadDWORD (   
   PROPID id,  
   DWORD* pValue  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `id`  
 in Der Bezeichner der zu lesenden Eigenschaft ( `PROPID` ist in Wtypes. h als definiert `ULONG` ).  
  
 `pValue`  
 vorgenommen Gibt den Eigenschafts Wert zurück.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird zurückgegeben `S_OK` ; andernfalls wird ein Fehlercode zurückgegeben. Gibt zurück, `E_INVALIDARG` Wenn die Eigenschaft nicht vom Typ ist `DWORD` .  
  
## <a name="remarks"></a>Bemerkungen  
 Eine `DWORD` wird von Windows als eine 32-Bit-Ganzzahl ohne Vorzeichen definiert.  
  
## <a name="see-also"></a>Weitere Informationen  
 [IDiaPropertyStorage](../../debugger/debug-interface-access/idiapropertystorage.md)
