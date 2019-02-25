---
title: IDebugDefaultPort2::QueryIsLocal | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDefaultPort2::QueryIsLocal
helpviewer_keywords:
- IDebugDefaultPort2::QueryIsLocal
ms.assetid: 1a42e774-c6ed-419a-a0e3-cab5778652ca
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1e9ca74b007c3da5ac3674813ff37c718cdd801e
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/22/2019
ms.locfileid: "56685533"
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