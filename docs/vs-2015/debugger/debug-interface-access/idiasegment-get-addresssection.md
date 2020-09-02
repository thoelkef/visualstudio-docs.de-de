---
title: 'IDiaSegment:: get_addressSection | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSegment::get_addressSection method
ms.assetid: 360b61b1-69b1-4a8b-ba37-97a1d835ac53
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 2f1dfe6971d4e5c57af0f350b9978a0081761f5d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68151812"
---
# <a name="idiasegmentget_addresssection"></a>IDiaSegment::get_addressSection
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Ruft die Abschnitts Nummer ab, die diesem Segment zugeordnet ist.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
HRESULT get_addressSection (   
   DWORD* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pRetVal`  
 vorgenommen Gibt die Abschnitts Nummer zurück, die diesem Segment zugeordnet ist.  
  
## <a name="return-value"></a>Rückgabewert  
 Gibt bei Erfolg `S_OK` zurück. Gibt zurück, `S_FALSE` Wenn diese Eigenschaft nicht unterstützt wird. Andernfalls wird ein Fehlercode zurückgegeben.  
  
## <a name="see-also"></a>Weitere Informationen  
 [IDiaSegment](../../debugger/debug-interface-access/idiasegment.md)
