---
title: 'IDebugEngine2:: abtexception | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngine2::SetException
helpviewer_keywords:
- IDebugEngine2::SetException
ms.assetid: e6f5ec48-09e8-4b9b-9dc9-55f8d883f1b7
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 7398db3c15c58821e05eff839a1022276401d569
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "80730933"
---
# <a name="idebugengine2setexception"></a>IDebugEngine2::SetException
Gibt an, wie die Debug-Engine (de) eine bestimmte Ausnahme behandeln soll.

## <a name="syntax"></a>Syntax

```cpp
HRESULT SetException( 
   EXCEPTION_INFO* pException
);
```

```csharp
int SetException( 
   EXCEPTION_INFO[] pException
);
```

## <a name="parameters"></a>Parameter
`pException`\
in Eine [EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md) -Struktur, die die Ausnahme beschreibt und debuggt.

## <a name="return-value"></a>Rückgabewert
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Bemerkungen
 Ein de könnte angewiesen werden, das Programm zu beenden, das eine Ausnahme bei der ersten Chance, der zweiten Gelegenheit oder überhaupt nicht auslöst.

## <a name="see-also"></a>Weitere Informationen
- [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)
- [EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md)
