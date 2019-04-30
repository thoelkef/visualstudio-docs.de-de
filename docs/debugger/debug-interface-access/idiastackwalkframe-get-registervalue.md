---
title: 'Idiastackwalkframe:: Get_registervalue | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackWalkFrame::get_registerValue method
ms.assetid: ca3c20a9-934a-4b2c-a7f6-7d06e8611ff2
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7d60fa2ebefb7e1e4eefccce866a1059fdbc78a1
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62837978"
---
# <a name="idiastackwalkframegetregistervalue"></a>IDiaStackWalkFrame::get_registerValue
Ruft den Wert eines Registers.

## <a name="syntax"></a>Syntax

```C++
HRESULT get_registerValue ( 
   DWORD      index,
   ULONGLONG* pRetVal
);
```

#### <a name="parameters"></a>Parameter
 `index`

[in] Ein Wert aus der [CV_HREG_e-Enumeration](../../debugger/debug-interface-access/cv-hreg-e.md) -Enumeration, die das Register, um den Wert für angibt.

 `pRetVal`

[out] Gibt den aktuellen Wert des Registers zurück.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird `S_OK`ist, andernfalls ein Fehlercode zurückgegeben.

## <a name="see-also"></a>Siehe auch
- [IDiaStackWalkFrame](../../debugger/debug-interface-access/idiastackwalkframe.md)
- [CV_HREG_e-Enumeration](../../debugger/debug-interface-access/cv-hreg-e.md)