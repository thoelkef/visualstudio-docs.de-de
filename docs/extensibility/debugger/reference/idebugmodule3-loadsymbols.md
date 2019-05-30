---
title: IDebugModule3::LoadSymbols | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugModule3::LoadSymbols
helpviewer_keywords:
- IDebugModule3::LoadSymbols
ms.assetid: 7548c8c1-cbc6-48aa-a845-19058d4a85bb
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: e1b23e7b1ae837087db198795ffeda6a5827f045
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/29/2019
ms.locfileid: "66323842"
---
# <a name="idebugmodule3loadsymbols"></a>IDebugModule3::LoadSymbols
Lädt die Symbole für das aktuelle Modul.

## <a name="syntax"></a>Syntax

```cpp
HRESULT LoadSymbols(
   void
);
```

```csharp
int LoadSymbols();
```

## <a name="return-value"></a>Rückgabewert
 Wenn die Methode erfolgreich ist, gibt es `S_OK`. Wenn ein Fehler auftritt, wird einen Fehlercode zurückgegeben.

## <a name="remarks"></a>Hinweise
 Diese Methode lädt die Symbole aus dem aktuellen Pfad für die Suche (das kann geändert werden, durch den Aufruf der [SetSymbolPath](../../../extensibility/debugger/reference/idebugengine3-setsymbolpath.md) Methode).

 Diese Methode ist vorzuziehen der [ReloadSymbols_Deprecated](../../../extensibility/debugger/reference/idebugmodule2-reloadsymbols-deprecated.md) Methode.

## <a name="see-also"></a>Siehe auch
- [IDebugModule3](../../../extensibility/debugger/reference/idebugmodule3.md)
- [SetSymbolPath](../../../extensibility/debugger/reference/idebugengine3-setsymbolpath.md)