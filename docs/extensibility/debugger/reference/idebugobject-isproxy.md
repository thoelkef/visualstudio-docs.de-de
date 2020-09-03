---
title: 'Idebugobject:: isproxy | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugObject::IsProxy
- IsProxy
ms.assetid: 06c66b87-db95-4400-ab26-5d33e743a439
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 6cab0d0d0f5f1c2e491c9aa0fe9efd26b39e51df
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "80726473"
---
# <a name="idebugobjectisproxy"></a>IDebugObject::IsProxy
Bestimmt, ob es sich bei dem Objekt um einen transparenten Proxy handelt.

## <a name="syntax"></a>Syntax

```cpp
HRESULT IsProxy (
   BOOL* pfIsProxy
);
```

```csharp
int IsProxy (
   out bool pfIsProxy
);
```

## <a name="parameters"></a>Parameter
`pfIsProxy`\
[out] `TRUE` , wenn das Objekt ein transparenter Proxy ist. andernfalls `FALSE` .

## <a name="return-value"></a>Rückgabewert
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Bemerkungen
 Diese Methode wird von der standardmäßigen C++-Debug-Engine implementiert.

## <a name="see-also"></a>Weitere Informationen
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)
