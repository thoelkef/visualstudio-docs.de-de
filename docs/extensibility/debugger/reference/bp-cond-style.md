---
title: BP_COND_STYLE | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BP_COND_STYLE
helpviewer_keywords:
- BP_COND_STYLE enumeration
ms.assetid: a93b1412-f447-48a1-af9d-38f3dbb3092f
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 70ab3655d27e810b3c05d0e0e81d81bc15a26950
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/22/2019
ms.locfileid: "56685858"
---
# <a name="bpcondstyle"></a>BP_COND_STYLE
Gibt den Haltepunkt-Bedingung-Stil für ausstehende und gebundene Haltepunkte.

## <a name="syntax"></a>Syntax

```cpp
enum enum_BP_COND_STYLE {
    BP_COND_NONE         = 0x0000,
    BP_COND_WHEN_TRUE    = 0x0001,
    BP_COND_WHEN_CHANGED = 0x0002
};
typedef DWORD BP_COND_STYLE;
```

```csharp
public enum enum_BP_COND_STYLE {
    BP_COND_NONE         = 0x0000,
    BP_COND_WHEN_TRUE    = 0x0001,
    BP_COND_WHEN_CHANGED = 0x0002
};
```

## <a name="members"></a>Member
BP_COND_NONE den Haltepunkt wird ausgelöst, bei Erreichen des Haltepunkts Position. Keine Bedingung für Haltepunkt angegeben.

BP_COND_WHEN_TRUE löst den Haltepunkt aus, nur wenn der bedingte Ausdruck mit dem Haltepunkt verknüpften ergibt `true`.

BP_COND_WHEN_CHANGED wird ausgelöst, die der Haltepunkt nur, wenn der Wert des bedingten Ausdrucks mit dem Haltepunkt zugeordneten aus der vorherigen Auswertung geändert wurde.

## <a name="remarks"></a>Hinweise
Verwendet für die `styleCondition` Mitglied der [BP_CONDITION](../../../extensibility/debugger/reference/bp-condition.md) Struktur.

## <a name="requirements"></a>Anforderungen
Header: msdbg.h

Namespace: Microsoft.VisualStudio.Debugger.Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Siehe auch
- [Enumerationen](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [BP_CONDITION](../../../extensibility/debugger/reference/bp-condition.md)
