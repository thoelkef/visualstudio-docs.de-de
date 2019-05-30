---
title: IDebugProgram2::GetMemoryBytes | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgram2::GetMemoryBytes
helpviewer_keywords:
- IDebugProgram2::GetMemoryBytes
ms.assetid: 1cdedb47-caf8-468e-aaf4-163f16afb403
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: ca06bd4593401544155e53c21315499d85edc07a
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/29/2019
ms.locfileid: "66319432"
---
# <a name="idebugprogram2getmemorybytes"></a>IDebugProgram2::GetMemoryBytes
Ruft das Byte Arbeitsspeicher durch das Programm ab.

## <a name="syntax"></a>Syntax

```cpp
HRESULT GetMemoryBytes( 
   IDebugMemoryBytes2** ppMemoryBytes
);
```

```csharp
int GetMemoryBytes( 
   out IDebugMemoryBytes2 ppMemoryBytes
);
```

## <a name="parameters"></a>Parameter
`ppMemoryBytes`\
[out] Gibt eine [IDebugMemoryBytes2](../../../extensibility/debugger/reference/idebugmemorybytes2.md) -Objekt, das die Bytes der Arbeitsspeicher des Programms darstellt.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird `S_OK`ist, andernfalls ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Hinweise
 Der Speicher-Bytes dargestellt durch die [IDebugMemoryBytes2](../../../extensibility/debugger/reference/idebugmemorybytes2.md) Objekt ist für das Programm Bild im Arbeitsspeicher und keinen Arbeitsspeicher, der belegt wurde, wenn das Programm ausgeführt wurde.

## <a name="see-also"></a>Siehe auch
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [IDebugMemoryBytes2](../../../extensibility/debugger/reference/idebugmemorybytes2.md)