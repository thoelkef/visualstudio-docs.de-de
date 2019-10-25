---
title: 'IDiaStackFrame:: get_rawLVarInstanceValue | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackFrame::get_rawLVarInstanceValue method
ms.assetid: ce526259-85a6-475b-9274-0b3a21d95db2
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0b1118517988f6a790cd4f6732eba3bc8a9fc25a
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/22/2019
ms.locfileid: "72741637"
---
# <a name="idiastackframeget_rawlvarinstancevalue"></a>IDiaStackFrame::get_rawLVarInstanceValue
Diese Methode ruft den Wert der angegebenen lokalen Variablen als Rohdaten Bytes ab.

## <a name="syntax"></a>Syntax

```C++
HRESULT get_rawLVarInstanceValue(
   IDiaLVarInstance* pInstance,
   DWORD             cbDataMax,
   DWORD*            pcbData,
   BYTE*             pbData
);
```

#### <a name="parameters"></a>Parameter
 `pInstance`

in Ein `IDiaLVarInstance` Objekt, das eine Instanz der lokalen Variablen darstellt, für die der Wert zu erhalten ist.

 `cbDataMax`

in Die maximale Anzahl von Bytes im Puffer, auf die durch `pbData` verwiesen wird. Dies kann ein Maximum von 8 Bytes (`sizeof(ULONGLONG)`) sein.

 `pcbData`

vorgenommen Gibt die tatsächliche Anzahl von Bytes zurück, die im Puffer gespeichert werden.

 `pbData`

vorgenommen Ein Puffer, der mit Daten aufgefüllt werden soll. Dieser darf nicht `NULL` sein.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird `S_OK` zurückgegeben. Andernfalls wird ein Fehlercode zurückgegeben.

## <a name="see-also"></a>Siehe auch
- [IDiaStackFrame](../../debugger/debug-interface-access/idiastackframe.md)