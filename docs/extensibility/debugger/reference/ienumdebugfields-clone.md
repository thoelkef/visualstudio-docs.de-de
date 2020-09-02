---
title: 'Ienumentbugfields:: Clone | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugFields::Clone
helpviewer_keywords:
- IEnumDebugFields::Clone method
ms.assetid: 7ec265a8-696f-45ce-a2a2-0a83e96fee1b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 1120e62d5dbed45f11b43ea0e131ee3173c1751c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "80716914"
---
# <a name="ienumdebugfieldsclone"></a>IEnumDebugFields::Clone
Diese Methode gibt eine Kopie der aktuellen Enumeration als separates Objekt zurück.

## <a name="syntax"></a>Syntax

```cpp
HRESULT Clone(
   IEnumDebugFields** ppEnum
);
```

```csharp
int Clone(
   out IEnumDebugFields ppEnum
);
```

## <a name="parameters"></a>Parameter
`ppEnum`\
[out] Gibt eine Kopie dieser Enumeration als ein separates Objekt zurück.

## <a name="property-valuereturn-value"></a>Eigenschaftswert/Rückgabewert
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Bemerkungen
 Die Kopie der-Enumeration hat denselben Zustand wie die ursprüngliche, wenn diese Methode aufgerufen wird. Allerdings sind die Status der Kopier-und ursprünglichen Zustände getrennt und können einzeln geändert werden.

## <a name="see-also"></a>Weitere Informationen
- [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)
