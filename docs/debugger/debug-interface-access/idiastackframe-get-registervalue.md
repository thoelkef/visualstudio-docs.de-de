---
title: 'Idiastackframe:: Get_registervalue | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackFrame::get_registerValue method
ms.assetid: cbe3d8ac-319a-40ac-bc3e-4eb81b2d7807
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a819293863b658f6e12609b2c1cd83c37532e02d
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 02/21/2019
ms.locfileid: "56637632"
---
# <a name="idiastackframegetregistervalue"></a>IDiaStackFrame::get_registerValue
Ruft den Wert eines angegebenen Registers ab, wie Sie in den Stapelrahmen gespeichert.

## <a name="syntax"></a>Syntax

```C++
HRESULT get_registerValue(
   ULONG      registerIndex,
   ULONGLONG *pRetVal
);
```

#### <a name="parameters"></a>Parameter
 `registerIndex`

[in] Eines der [CV_HREG_e-Enumeration](../../debugger/debug-interface-access/cv-hreg-e.md) -Enumerationswerte fest.

 `pRetVal`

[out] Der Wert im Register gespeichert.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird `S_OK`ist, andernfalls gibt den Fehlercode zurück.

## <a name="see-also"></a>Siehe auch
- [IDiaStackFrame](../../debugger/debug-interface-access/idiastackframe.md)
- [CV_HREG_e-Enumeration](../../debugger/debug-interface-access/cv-hreg-e.md)