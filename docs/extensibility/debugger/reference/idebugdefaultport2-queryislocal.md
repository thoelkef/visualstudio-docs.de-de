---
title: IDebugDefaultPort2::QueryIsLocal | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDefaultPort2::QueryIsLocal
helpviewer_keywords:
- IDebugDefaultPort2::QueryIsLocal
ms.assetid: 1a42e774-c6ed-419a-a0e3-cab5778652ca
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 42a21419af9be56647a835ee1d8ddab62e20f842
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/29/2019
ms.locfileid: "66351753"
---
# <a name="idebugdefaultport2queryislocal"></a>IDebugDefaultPort2::QueryIsLocal
Diese Methode bestimmt, ob dieser Port auf dem lokalen Computer ist.

## <a name="syntax"></a>Syntax

```cpp
HRESULT QueryIsLocal(
   void
);
```

```csharp
int QueryIsLocal();
```

## <a name="return-value"></a>Rückgabewert
 Gibt `S_OK` ist dieser Port lokaler (auf dem gleichen Computer wie der Aufrufer) oder `S_FALSE` Wenn Port auf einem anderen Computer verwendet wird.

## <a name="see-also"></a>Siehe auch
- [IDebugDefaultPort2](../../../extensibility/debugger/reference/idebugdefaultport2.md)