---
title: 'IDebugPort2:: GetProcess | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPort2::GetPortSupplier
helpviewer_keywords:
- IDebugPort2::GetPortSupplier
ms.assetid: 3e2431b0-0e19-450d-8e1d-d7c314c8f872
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 4496187fd2e8f86a64e85afc8a4cb00eb589696a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "80725258"
---
# <a name="idebugport2getprocess"></a>IDebugPort2::GetProcess
Ruft den angegebenen Prozess ab, der auf einem Port ausgeführt wird.

## <a name="syntax"></a>Syntax

```cpp
HRESULT GetProcess( 
   AD_PROCESS_ID    ProcessId,
   IDebugProcess2** ppProcess
);
```

```csharp
int GetProcess( 
   AD_PROCESS_ID      ProcessId,
   out IDebugProcess2 ppProcess
);
```

## <a name="parameters"></a>Parameter
`ProcessId`\
in Eine [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md) -Struktur, die den Prozess Bezeichner angibt.

`ppProcess`\
vorgenommen Gibt ein [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md) -Objekt zurück, das den Prozess darstellt.

## <a name="return-value"></a>Rückgabewert
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.

## <a name="see-also"></a>Weitere Informationen
- [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)
- [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)
- [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md)
