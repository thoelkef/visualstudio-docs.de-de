---
title: IDiaStackWalkHelper::p ut_registervalue | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackWalkHelper2::put_registerValue method
ms.assetid: 8f02ce54-ef59-455f-8aa6-dc26761c7aff
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 619ed78584a9fe897b19d6ac2ffd4c28838c61ab
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/22/2019
ms.locfileid: "72741368"
---
# <a name="idiastackwalkhelperput_registervalue"></a>IDiaStackWalkHelper::put_registerValue
Legt den Wert eines Register fest.

## <a name="syntax"></a>Syntax

```C++
HRESULT put_registerValue ( 
   DWORD     index,
   ULONGLONG NewVal
);
```

#### <a name="parameters"></a>Parameter
 `index`

in Ein Wert aus der [CV_HREG_e](../../debugger/debug-interface-access/cv-hreg-e.md) -enumerationsenumeration, die das Register angibt, in das geschrieben werden soll.

 `NewVal`

in Der neue Registrierungs Wert.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird `S_OK` zurückgegeben. Andernfalls wird ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Hinweise
 Trotz der Größe des Werts sollte in einer-Implementierung nur das, was das Register normalerweise enthält, gespeichert werden. Beispielsweise würde ein 8-Bit-Register nur die niedrigsten 8 Bits des angegebenen Werts enthalten.

## <a name="see-also"></a>Siehe auch
- [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md)
- [CV_HREG_e-Enumeration](../../debugger/debug-interface-access/cv-hreg-e.md)