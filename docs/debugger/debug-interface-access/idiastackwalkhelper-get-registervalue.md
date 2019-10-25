---
title: 'IDiaStackWalkHelper:: get_registerValue | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackWalkHelper2::get_registerValue method
ms.assetid: 46ac5eee-73a3-44a1-8635-6c58ba193cb6
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: bfb3e219012effe47a2352f7c22c6cf51b4617f9
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/22/2019
ms.locfileid: "72741415"
---
# <a name="idiastackwalkhelperget_registervalue"></a>IDiaStackWalkHelper::get_registerValue
Ruft den Wert eines Register ab.

## <a name="syntax"></a>Syntax

```C++
HRESULT get_registerValue ( 
   DWORD      index,
   ULONGLONG* pRetVal
);
```

#### <a name="parameters"></a>Parameter
 `index`

in Ein Wert aus der [CV_HREG_e](../../debugger/debug-interface-access/cv-hreg-e.md) -enumerationsenumeration, die angibt, von welchem Register der Wert abgeleitet werden soll.

 `pRetVal`

vorgenommen Gibt den aktuellen Wert des Register zurück.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird `S_OK` zurückgegeben. Andernfalls wird ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Hinweise
 Trotz der Größe des `pRetVal`-Parameters sollte eine-Implementierung nur das, was das Register normalerweise enthält, speichern. Ein 8-Bit-Register enthält z. b. nur die niedrigsten 8 Bits des angegebenen-Werts. Dieser 8-Bit-Wert wird auf 64 Bit erweitert, wenn er von dieser Methode zurückgegeben wird.

## <a name="see-also"></a>Siehe auch
- [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md)
- [CV_HREG_e-Enumeration](../../debugger/debug-interface-access/cv-hreg-e.md)