---
title: 'IDiaStackFrame:: get_registerValue | Microsoft-Dokumentation'
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
ms.openlocfilehash: d270b9b177367c9a15c2b64f6f8bc5607c5a459d
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/22/2019
ms.locfileid: "72741620"
---
# <a name="idiastackframeget_registervalue"></a>IDiaStackFrame::get_registerValue
Ruft den Wert eines angegebenen Registers ab, wie er im Stapel Rahmen gespeichert ist.

## <a name="syntax"></a>Syntax

```C++
HRESULT get_registerValue(
   ULONG      registerIndex,
   ULONGLONG *pRetVal
);
```

#### <a name="parameters"></a>Parameter
 `registerIndex`

in Einer der Enumerationswerte der [CV_HREG_e-Enumeration](../../debugger/debug-interface-access/cv-hreg-e.md) .

 `pRetVal`

vorgenommen Im Register gespeicherter Wert.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird `S_OK` zurückgegeben. Andernfalls wird der Fehlercode zurückgegeben.

## <a name="see-also"></a>Siehe auch
- [IDiaStackFrame](../../debugger/debug-interface-access/idiastackframe.md)
- [CV_HREG_e-Enumeration](../../debugger/debug-interface-access/cv-hreg-e.md)