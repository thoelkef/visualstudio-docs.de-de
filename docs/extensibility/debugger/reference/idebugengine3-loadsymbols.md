---
title: IDebugEngine3::LoadSymbols | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngine3::LoadSymbols
helpviewer_keywords:
- IDebugEngine3::LoadSymbols
ms.assetid: c846a440-1d91-4d48-b8f1-82e902ae152b
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ff317b217b72fcb5a6042747abd88e5a9d344f7a
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62875353"
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

#### <a name="parameters"></a>Parameter
 Keine

## <a name="return-value"></a>Rückgabewert
 Im Erfolgsfall gibt S_OK zurück. Andernfalls wird Fehlercode zurückgegeben.

## <a name="remarks"></a>Hinweise
 Dadurch wird die Debugsymbole für alle Module, die auf die verwiesen wird durch diese Debug-Engine geladen. Nur dann, wenn sie noch nicht geladen wurden, werden die Symbole geladen. Symbole werden durchsucht, auf den Pfaden, die festlegen, die durch einen Aufruf von [SetSymbolPath](../../../extensibility/debugger/reference/idebugengine3-setsymbolpath.md).

## <a name="see-also"></a>Siehe auch
- [SetSymbolPath](../../../extensibility/debugger/reference/idebugengine3-setsymbolpath.md)
- [IDebugEngine3](../../../extensibility/debugger/reference/idebugengine3.md)