---
title: IDebugEngine3::LoadSymbols | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngine3::LoadSymbols
helpviewer_keywords:
- IDebugEngine3::LoadSymbols
ms.assetid: c846a440-1d91-4d48-b8f1-82e902ae152b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 7963d39601a0d3a90ca2daa7632902d7aa506de8
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80730814"
---
# <a name="idebugengine3loadsymbols"></a>IDebugEngine3::LoadSymbols
Lädt (bei Bedarf) Symbole für alle Module, die von diesem Debugging-Modul gedebuggt werden.

## <a name="syntax"></a>Syntax

```cpp
HRESULT LoadSymbols();
```

```csharp
int LoadSymbols();
```

## <a name="parameters"></a>Parameter
 Keine.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, kehrt S_OK zurück; Andernfalls wird Fehlercode zurückgegeben.

## <a name="remarks"></a>Bemerkungen
 Dadurch werden Debugsymbole für alle Module geladen, auf die von diesem Debuggingmodul verwiesen wird. Die Symbole werden nur geladen, wenn sie noch nicht geladen wurden. Symbole werden auf den Pfaden durchsucht, die durch einen Aufruf von [SetSymbolPath](../../../extensibility/debugger/reference/idebugengine3-setsymbolpath.md)festgelegt wurden.

## <a name="see-also"></a>Weitere Informationen
- [SetSymbolPath](../../../extensibility/debugger/reference/idebugengine3-setsymbolpath.md)
- [IDebugEngine3](../../../extensibility/debugger/reference/idebugengine3.md)
