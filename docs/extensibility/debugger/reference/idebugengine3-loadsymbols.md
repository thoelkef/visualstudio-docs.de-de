---
title: IDebugEngine3::LoadSymbols | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngine3::LoadSymbols
helpviewer_keywords:
- IDebugEngine3::LoadSymbols
ms.assetid: c846a440-1d91-4d48-b8f1-82e902ae152b
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 72c4fce5a7e8dd53093e21db2771d2176462e67c
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/29/2019
ms.locfileid: "66352526"
---
# <a name="idebugengine3loadsymbols"></a>IDebugEngine3::LoadSymbols
Lädt (nach Bedarf)-Symbole für alle Module, die durch diese Debug-Engine gedebuggt wird.

## <a name="syntax"></a>Syntax

```cpp
HRESULT LoadSymbols();
```

```csharp
int LoadSymbols();
```

## <a name="parameters"></a>Parameter
 Keine

## <a name="return-value"></a>Rückgabewert
 Im Erfolgsfall gibt S_OK zurück. Andernfalls wird Fehlercode zurückgegeben.

## <a name="remarks"></a>Hinweise
 Dadurch wird die Debugsymbole für alle Module, die auf die verwiesen wird durch diese Debug-Engine geladen. Nur dann, wenn sie noch nicht geladen wurden, werden die Symbole geladen. Symbole werden durchsucht, auf den Pfaden, die festlegen, die durch einen Aufruf von [SetSymbolPath](../../../extensibility/debugger/reference/idebugengine3-setsymbolpath.md).

## <a name="see-also"></a>Siehe auch
- [SetSymbolPath](../../../extensibility/debugger/reference/idebugengine3-setsymbolpath.md)
- [IDebugEngine3](../../../extensibility/debugger/reference/idebugengine3.md)