---
title: 'Idiapropertystorage:: Read-OL | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaPropertyStorage::ReadBOOL
ms.assetid: ad1822db-4572-48f7-9919-f8137f6701f2
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 64eee421a5ed5bd46a64b51694d913a4f2dc4d41
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "62538875"
---
# <a name="idiapropertystoragereadbool"></a>IDiaPropertyStorage::ReadBOOL
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Liest `BOOL` Werte in einem Eigenschaften Satz.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
HRESULT ReadBOOL (   
   PROPID id,  
   BOOL*  pValue  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `id`  
 in Der Bezeichner der zu lesenden Eigenschaft ( `PROPID` ist in Wtypes. h als definiert `ULONG` ).  
  
 `pValue`  
 vorgenommen Gibt den Eigenschafts Wert zurück.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird zurückgegeben `S_OK` ; andernfalls wird ein Fehlercode zurückgegeben. Gibt zurück, `E_INVALIDARG` Wenn die Eigenschaft nicht vom Typ ist `BOOL` .  
  
## <a name="remarks"></a>Bemerkungen  
 Um konsistente Ergebnisse zu erzielen, interpretieren Sie den `BOOL` Wert so, dass Werte ungleich NULL `TRUE` und NULL gleich sind `FALSE` .  
  
## <a name="see-also"></a>Weitere Informationen  
 [IDiaPropertyStorage](../../debugger/debug-interface-access/idiapropertystorage.md)
