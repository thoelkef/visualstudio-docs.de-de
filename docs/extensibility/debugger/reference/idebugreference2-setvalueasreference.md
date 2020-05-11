---
title: IDebugReference2::SetValueAsReferenz | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugReference2::SetValueAsReference
helpviewer_keywords:
- IDebugReference2::SetValueAsReference
ms.assetid: 94a545d2-16b9-45e9-b2e7-4e49ff90aad0
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: f4767dbe08e716d64ea03c18a1c4a6f7d6690a7b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80720307"
---
# <a name="idebugreference2setvalueasreference"></a>IDebugReference2::SetValueAsReference
Legt den Wert eines Verweises aus einem anderen Verweis fest. Für die zukünftige Verwendung reserviert.

## <a name="syntax"></a>Syntax

```cpp
HRESULT SetValueAsReference ( 
   IDebugReference2** rgpArgs,
   DWORD              dwArgCount,
   IDebugReference2*  pValue,
   DWORD              dwTimeout
);
```

```cpp
int SetValueAsReference ( 
   IDebugReference2[] rgpArgs,
   uint               dwArgCount,
   IDebugReference2   pValue,
   uint               dwTimeout
);
```

## <a name="parameters"></a>Parameter
`rgpArgs`\
[in] Ein Array von [IDebugReference2-Objekten,](../../../extensibility/debugger/reference/idebugreference2.md) die verwendet werden, um zu bestimmen, wie der Referenzwert festgelegt wird.

`dwArgCount`\
[in] Die Anzahl der Verweise im Array.

`pValue`\
[in] Ein [IDebugReference2-Objekt,](../../../extensibility/debugger/reference/idebugreference2.md) von dem aus der Eigenschaftswert festgelegt werden soll.

`dwTimeout`\
[in] Maximale Wartezeit in Millisekunden, bevor von dieser Methode zurückgegeben wird. Verwenden `INFINITE` Sie diese Verwendung, um auf unbestimmte Zeit zu warten.

## <a name="return-value"></a>Rückgabewert
 Gibt immer `E_NOTIMPL` zurück.

## <a name="see-also"></a>Weitere Informationen
- [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)
