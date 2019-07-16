---
title: IDebugProgramHost2::GetHostId | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramHost2::GetHostId
helpviewer_keywords:
- IDebugProgramHost2::GetHostId
ms.assetid: 7702e221-feb1-446b-a224-cb46c420987e
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 94ed7ae7b46fc9fbc3a37472bd3464f30c35acf8
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/29/2019
ms.locfileid: "66325198"
---
# <a name="idebugprogramhost2gethostid"></a>IDebugProgramHost2::GetHostId
Ruft die Prozess-ID von der Hostprozess für dieses Programm ab.

## <a name="syntax"></a>Syntax

```cpp
HRESULT GetHostId( 
   AD_PROCESS_ID* pdwId
);
```

```csharp
int GetHostId( 
   AD_PROCESS_ID[] pdwId
);
```

## <a name="parameters"></a>Parameter
`pdwId`\
[in, out] Ein [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md) -Struktur, die mit die Prozess-ID-Informationen gefüllt wird.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird `S_OK`ist, andernfalls ein Fehlercode zurückgegeben.

## <a name="see-also"></a>Siehe auch
- [IDebugProgramHost2](../../../extensibility/debugger/reference/idebugprogramhost2.md)
- [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md)