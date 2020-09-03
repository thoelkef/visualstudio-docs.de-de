---
title: 'IDebugStackFrame2:: getphysicalstackrange | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugStackFrame2::GetPhysicalStackRange
helpviewer_keywords:
- IDebugStackFrame2::GetPhysicalStackRange
ms.assetid: 2f6992e2-ac1c-433f-83b7-a7f83a4ce63d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 3df924c6c8a4373082d61575e4ad8a7ec3f161d1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "80719669"
---
# <a name="idebugstackframe2getphysicalstackrange"></a>IDebugStackFrame2::GetPhysicalStackRange
Ruft eine Computer abhängige Darstellung des Bereichs physischer Adressen ab, der einem Stapel Rahmen zugeordnet ist.

## <a name="syntax"></a>Syntax

```cpp
HRESULT GetPhysicalStackRange ( 
   UINT64* paddrMin,
   UINT64* paddrMax
);
```

```csharp
int GetPhysicalStackRange ( 
   out ulong paddrMin,
   out ulong paddrMax
);
```

## <a name="parameters"></a>Parameter
`paddrMin`\
vorgenommen Gibt die niedrigste physische Adresse zurück, die diesem Stapel Rahmen zugeordnet ist.

`paddrMax`\
vorgenommen Gibt die höchste physische Adresse zurück, die diesem Stapel Rahmen zugeordnet ist.

## <a name="return-value"></a>Rückgabewert
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Bemerkungen
 Die von dieser Methode zurückgegebenen Informationen werden vom Sitzungs-Debug-Manager (SDM) zum Sortieren von Stapel Rahmen verwendet.

 Es wird davon ausgegangen, dass die aufrufsstapel nach unten wächst, d. h., dass neue Stapel Rahmen bei immer niedrigeren Speicheradressen hinzugefügt werden. Eine Lauf Zeit Architektur muss physische Stapel Bereiche bereitstellen, die dieser Annahme entsprechen.

## <a name="see-also"></a>Weitere Informationen
- [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)
