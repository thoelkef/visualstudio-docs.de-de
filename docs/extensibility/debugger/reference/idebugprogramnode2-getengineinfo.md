---
title: IDebugProgramNode2::GetEngineInfo | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramNode2::GetEngineInfo
helpviewer_keywords:
- IDebugProgramNode2::GetEngineInfo
ms.assetid: 664e7fe5-9100-4b7d-9dc5-e5a4dd0d0451
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 421eea42c169f586657998e5d4cd57c4c797b71e
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/22/2019
ms.locfileid: "56693190"
---
# <a name="idebugprogramnode2getengineinfo"></a>IDebugProgramNode2::GetEngineInfo
Ruft den Namen und Bezeichner des Debug-Engine (DE) ein Programm ausgeführt wird.

## <a name="syntax"></a>Syntax

```cpp
HRESULT GetEngineInfo ( 
   BSTR* pbstrEngine,
   GUID* pguidEngine
);
```

```csharp
int GetEngineInfo(
   out string pbstrEngine,
   out Guid pguidEngine
);
```

#### <a name="parameters"></a>Parameter
 `pbstrEngine`

 [out] Gibt den Namen der Ausführung des Programms DE zurück (C++-spezifischen: Dies kann ein null-Zeiger, der angibt, dass der Aufrufer nicht den Namen der Engine interessiert sein).

 `pguidEngine`

 [out] Gibt den globally unique Identifier des DE Ausführung des Programms (C++-spezifischen: Dies kann ein null-Zeiger, der angibt, dass der Aufrufer nicht der GUID des Moduls interessiert sein).

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird `S_OK`ist, andernfalls ein Fehlercode zurückgegeben.

## <a name="see-also"></a>Siehe auch
- [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)