---
title: IDebugProgram2::GetEngineInfo | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgram2::GetEngineInfo
helpviewer_keywords:
- IDebugProgram2::GetEngineInfo
ms.assetid: 3a4f2dc0-e082-4d8d-aeaf-463ab09d279b
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2b7a866730be3e6dfce8d68c655eb1f1b4d3f4da
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "68148711"
---
# <a name="idebugprogram2getengineinfo"></a>IDebugProgram2::GetEngineInfo
Ruft den Namen und GUID der Debug-Engine (DE) dieses Programm ausführen.

## <a name="syntax"></a>Syntax

```cpp
HRESULT GetEngineInfo( 
   BSTR* pbstrEngine,
   GUID* pguidEngine
);
```

```csharp
int GetEngineInfo( 
   out string pbstrEngine,
   out GUID   pguidEngine
);
```

#### <a name="parameters"></a>Parameter
 `pbstrEngine`

 [out] Gibt den Namen des DE dieses Programm ausführen.

 `pguidEngine`

 [out] Gibt die GUID der Ausführung dieses Programms DE zurück.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird `S_OK`ist, andernfalls ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Hinweise
 Jede DE definiert eine eigene GUID zur Identifikation.

## <a name="see-also"></a>Siehe auch
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)