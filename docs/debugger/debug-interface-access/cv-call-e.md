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
ms.openlocfilehash: 9d8c11e84a514739049a044a12ae482f7b2d9929
ms.sourcegitcommit: 752f03977f45169585e407ef719450dbe219b7fc
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 02/15/2019
ms.locfileid: "56316181"
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
CV_CALL_NEAR_C  
Gibt an, eine funktionsaufrufkonvention einen Nahen rechts-nach-links-Push verwenden. Die aufrufende Funktion löscht den Stapel.

CV_CALL_NEAR_FAST  
Gibt an, eine funktionsaufrufkonvention registriert einen nahezu links-nach-rechts-Push mit. Die aufgerufene Funktion verwendet die Summe der Parameter-Bytes auf den Stapel gelöscht.

CV_CALL_NEAR_STD  
Gibt an, eine funktionsaufrufkonvention mit nahezu Standardaufruf (rechts-nach-links-Push).

CV_CALL_NEAR_SYS  
Gibt an, eine funktionsaufrufkonvention mithilfe eines near Systemaufrufs.

CV_CALL_THISCALL  
Gibt einen Funktionsaufruf Konvention über `this` aufrufen (`this` Zeiger im Register übergeben).

CV_CALL_CLRCALL  
Gibt an, eine funktionsaufrufkonvention verwendet durch die Common Language Runtime (CLR) (auch bekannt als ein verwalteter Code Aufrufkonvention).

## <a name="remarks"></a>Anmerkungen
Die Werte in dieser Enumeration werden zurückgegeben, durch einen Aufruf der [idiasymbol:: Get_callingconvention](../../debugger/debug-interface-access/idiasymbol-get-callingconvention.md) Methode.

## <a name="requirements"></a>Anforderungen
Header: cvconst.h

## <a name="see-also"></a>Siehe auch
[Enumerationen und Strukturen](../../debugger/debug-interface-access/enumerations-and-structures.md)  
[IDiaSymbol::get_callingConvention](../../debugger/debug-interface-access/idiasymbol-get-callingconvention.md)
