---
title: IDebugMemoryContext2::Hinzufügen | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugMemoryContext2::Add
helpviewer_keywords:
- IDebugMemoryContext2::Add method
- Add method
ms.assetid: 3c47e646-ce9e-4dd3-8f1a-6dbd3827d407
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: a21fa2ec6d48bb1d6bf17bbc0d2ebf0d90a25a9f
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80727485"
---
# <a name="idebugmemorycontext2add"></a>IDebugMemoryContext2::Add
Fügt den angegebenen Wert zum aktuellen Kontext hinzu und gibt einen neuen Kontext zurück.

## <a name="syntax"></a>Syntax

```cpp
HRESULT Add( 
   UINT64                 dwCount,
   IDebugMemoryContext2** ppMemCxt
);
```

```csharp
int Add(
   ulong                    dwCount,
   out IDebugMemoryContext2 ppMemCxt
);
```

## <a name="parameters"></a>Parameter
`dwCount`\
[in] Der Wert, der dem aktuellen Kontext hinzugefügt werden soll.

`ppMemCxt`\
[out] Gibt ein neues [IDebugMemoryContext2-Objekt](../../../extensibility/debugger/reference/idebugmemorycontext2.md) zurück.

## <a name="return-value"></a>Rückgabewert
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Bemerkungen
 Ein Speicherkontext ist eine Adresse, sodass das Hinzufügen eines Werts zu einer Adresse eine neue Adresse erzeugt, die eine neue Kontextschnittstelle erfordert.

 Diese Methode muss immer einen neuen Kontext erzeugen, auch wenn sich die resultierende Adresse außerhalb des speicherbereichs befindet, der diesem Kontext zugeordnet ist. Die einzige Ausnahme besteht darin, dass für den neuen `ppMemCxt` Kontext kein Speicher reserviert werden kann oder wenn es sich um einen NULL-Wert handelt (ein Fehler).

## <a name="see-also"></a>Weitere Informationen
- [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)
