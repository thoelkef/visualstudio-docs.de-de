---
title: CV_call_e | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- CV_call_e enumeration
ms.assetid: f230560b-4243-432d-8f19-46df112043b9
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5deb59d4bbee06e505ba10bf1d4f08b1b06aa62d
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/22/2019
ms.locfileid: "72745351"
---
# <a name="cv_call_e"></a>CV_call_e
Gibt die Aufruf Konvention für eine Funktion an.

> [!NOTE]
> Nur die am häufigsten aufgelisteten Enumerationswerte werden hier dokumentiert. Die gesamte Enumeration ist in der Header Datei "cvrest. h" verfügbar.

## <a name="syntax"></a>Syntax

```C++
typedef enum CV_call_e {
    CV_CALL_NEAR_C    = 0x00,
    CV_CALL_NEAR_FAST = 0x04,
    CV_CALL_NEAR_STD  = 0x07,
    CV_CALL_NEAR_SYS  = 0x09,
    CV_CALL_THISCALL  = 0x0b,
    CV_CALL_CLRCALL   = 0x16
} CV_call_e;
```

## <a name="elements"></a>Elements
CV_CALL_NEAR_C gibt eine Funktionsaufruf Konvention mit einem Push von rechts nach links an. Die Aufruf Funktion löscht den Stapel.

CV_CALL_NEAR_FAST gibt eine Funktionsaufruf Konvention mit einem Push von links nach rechts mit Registern an. Die aufgerufene Funktion verwendet die Summe der Parameter bytes, um den Stapel zu löschen.

CV_CALL_NEAR_STD gibt eine Funktionsaufruf Konvention mithilfe eines fast standardmäßigen Aufrufs an (von rechts nach links).

CV_CALL_NEAR_SYS gibt eine Funktionsaufruf Konvention mithilfe eines near-Systemaufrufs an.

CV_CALL_THISCALL gibt eine Funktionsaufruf Konvention mithilfe `this`-Aufrufs an (`this` Zeiger, der im Register übergebenen wird).

CV_CALL_CLRCALL gibt eine Funktionsaufruf Konvention an, die von der Common Language Runtime (CLR) verwendet wird (auch bekannt als Aufruf Konvention mit verwaltetem Code).

## <a name="remarks"></a>Hinweise
Die Werte in dieser Enumeration werden von einem Rückruf der [idiasymmetribol:: get_callingConvention](../../debugger/debug-interface-access/idiasymbol-get-callingconvention.md) -Methode zurückgegeben.

## <a name="requirements"></a>Anforderungen
Header: cvconst.h

## <a name="see-also"></a>Siehe auch
- [Enumerationen und Strukturen](../../debugger/debug-interface-access/enumerations-and-structures.md)
- [IDiaSymbol::get_callingConvention](../../debugger/debug-interface-access/idiasymbol-get-callingconvention.md)
