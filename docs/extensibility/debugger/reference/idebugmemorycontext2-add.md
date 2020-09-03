---
title: 'IDebugMemoryContext2:: Add | Microsoft-Dokumentation'
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "80727485"
---
# <a name="idebugmemorycontext2add"></a>IDebugMemoryContext2::Add
Fügt dem aktuellen Kontext den angegebenen Wert hinzu und gibt einen neuen Kontext zurück.

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
in Der Wert, der dem aktuellen Kontext hinzugefügt werden soll.

`ppMemCxt`\
vorgenommen Gibt ein neues [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md) -Objekt zurück.

## <a name="return-value"></a>Rückgabewert
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Bemerkungen
 Ein Speicher Kontext ist eine Adresse. das Hinzufügen eines Werts zu einer Adresse erzeugt also eine neue Adresse, die eine neue Kontext Schnittstelle erfordert.

 Diese Methode muss immer einen neuen Kontext ergeben, auch wenn sich die resultierende Adresse außerhalb des Speicherplatzes befindet, der diesem Kontext zugeordnet ist. Die einzige Ausnahme ist, wenn kein Arbeitsspeicher für den neuen Kontext zugeordnet werden kann oder wenn `ppMemCxt` ein NULL-Wert ist (bei dem es sich um einen Fehler handelt).

## <a name="see-also"></a>Weitere Informationen
- [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)
