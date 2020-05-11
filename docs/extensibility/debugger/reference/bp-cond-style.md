---
title: BP_COND_STYLE | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BP_COND_STYLE
helpviewer_keywords:
- BP_COND_STYLE enumeration
ms.assetid: a93b1412-f447-48a1-af9d-38f3dbb3092f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: ca704ca186308ea9e44c4fa7edc6617cbac806eb
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738114"
---
# <a name="bp_cond_style"></a>BP_COND_STYLE
Gibt den Haltepunktbedingungsstil für ausstehende und gebundene Haltepunkte an.

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

## <a name="fields"></a>Felder
`BP_COND_NONE`\
Feuert den Haltepunkt aus, wenn die Position des Haltepunkts erreicht ist. Es wurde keine Haltepunktbedingung angegeben.

`BP_COND_WHEN_TRUE`\
Gibt den Haltepunkt nur aus, wenn der dem `true`Haltepunkt zugeordnete bedingte Ausdruck zu ausgewertet wird.

`BP_COND_WHEN_CHANGED`\
Gibt den Haltepunkt nur aus, wenn sich der Wert des bedingten Ausdrucks, der dem Haltepunkt zugeordnet ist, gegenüber der vorherigen Auswertung geändert hat.

## <a name="remarks"></a>Bemerkungen
Wird für `styleCondition` das Element der [BP_CONDITION-Struktur](../../../extensibility/debugger/reference/bp-condition.md) verwendet.

## <a name="requirements"></a>Requirements (Anforderungen)
Kopfzeile: msdbg.h

Namespace: Microsoft.VisualStudio.Debugger.Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Weitere Informationen
- [Enumerationen](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [BP_CONDITION](../../../extensibility/debugger/reference/bp-condition.md)
