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
ms.openlocfilehash: ec5fea99994b891250dad85cfc43320848df98f9
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62555103"
---
# <a name="cvcalle"></a>CV_call_e
Gibt die Aufrufkonvention für eine Funktion an.

> [!NOTE]
> Nur die am häufigsten verwendeten Enumerationswerte sind hier dokumentiert. Die vollständige Enumeration ist in der Headerdatei cvconst.h verfügbar.

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
CV_CALL_NEAR_C gibt an, eine funktionsaufrufkonvention einen Nahen rechts-nach-links-Push verwenden. Die aufrufende Funktion löscht den Stapel.

Eine funktionsaufrufkonvention mithilfe einer nahezu links-nach-rechts-push-CV_CALL_NEAR_FAST gibt an, die registriert werden. Die aufgerufene Funktion verwendet die Summe der Parameter-Bytes auf den Stapel gelöscht.

CV_CALL_NEAR_STD gibt an, eine funktionsaufrufkonvention mit nahezu Standardaufruf (rechts-nach-links-Push).

Rufen Sie eine funktionsaufrufkonvention mithilfe eines near vom Systems CV_CALL_NEAR_SYS angibt.

CV_CALL_THISCALL gibt an, eine funktionsaufrufkonvention mit `this` aufrufen (`this` Zeiger im Register übergeben).

CV_CALL_CLRCALL gibt an, eine funktionsaufrufkonvention verwendet durch die Common Language Runtime (CLR) (auch bekannt als ein verwalteter Code Aufrufkonvention).

## <a name="remarks"></a>Hinweise
Die Werte in dieser Enumeration werden zurückgegeben, durch einen Aufruf der [idiasymbol:: Get_callingconvention](../../debugger/debug-interface-access/idiasymbol-get-callingconvention.md) Methode.

## <a name="requirements"></a>Anforderungen
Header: cvconst.h

## <a name="see-also"></a>Siehe auch
- [Enumerationen und Strukturen](../../debugger/debug-interface-access/enumerations-and-structures.md)
- [IDiaSymbol::get_callingConvention](../../debugger/debug-interface-access/idiasymbol-get-callingconvention.md)
