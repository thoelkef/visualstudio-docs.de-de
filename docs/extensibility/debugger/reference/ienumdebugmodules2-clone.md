---
title: 'IEnumDebugModules2:: Clone | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugModules2::Clone
helpviewer_keywords:
- IEnumDebugModules2::Clone
ms.assetid: fd6d3abc-20d9-4f6f-9c8e-5bd29f68d47d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 77dd68fadad5300a7a96787d91fbb17d9d456f60
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "80716603"
---
# <a name="ienumdebugmodules2clone"></a>IEnumDebugModules2::Clone
Gibt eine Kopie der aktuellen Enumeration als ein separates Objekt zurück.

## <a name="syntax"></a>Syntax

```cpp
HRESULT Clone(
   IEnumDebugModules2** ppEnum
);
```

```csharp
int Clone(
   out IEnumDebugModules2 ppEnum
);
```

## <a name="parameters"></a>Parameter
`ppEnum`\
[out] Gibt eine Kopie dieser Enumeration als ein separates Objekt zurück.

## <a name="return-value"></a>Rückgabewert
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Bemerkungen
 Die Kopie der-Enumeration hat denselben Zustand wie die ursprüngliche, wenn diese Methode aufgerufen wird. Allerdings sind die Status der Kopier-und ursprünglichen Zustände getrennt und können einzeln geändert werden.

## <a name="see-also"></a>Weitere Informationen
- [IEnumDebugModules2](../../../extensibility/debugger/reference/ienumdebugmodules2.md)
