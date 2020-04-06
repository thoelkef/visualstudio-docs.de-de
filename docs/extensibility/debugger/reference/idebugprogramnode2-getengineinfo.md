---
title: IDebugProgramNode2::GetEngineInfo | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramNode2::GetEngineInfo
helpviewer_keywords:
- IDebugProgramNode2::GetEngineInfo
ms.assetid: 664e7fe5-9100-4b7d-9dc5-e5a4dd0d0451
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: c2e74ba3c0f826314818bc883778a6364ff3fb6e
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80722100"
---
# <a name="idebugprogramnode2getengineinfo"></a>IDebugProgramNode2::GetEngineInfo
Ruft den Namen und den Bezeichner des Debugmoduls (DE) ab, das ein Programm ausführt.

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

## <a name="parameters"></a>Parameter
`pbstrEngine`\
[out] Gibt den Namen der DE zurück, die das Programm ausführt (C++-spezifisch: Dies kann ein Nullzeiger sein, der angibt, dass der Aufrufer nicht an dem Namen des Moduls interessiert ist).

`pguidEngine`\
[out] Gibt den global eindeutigen Bezeichner der DE zurück, die das Programm ausführt (C++-spezifisch: Dies kann ein Nullzeiger sein, der angibt, dass der Aufrufer nicht an der GUID des Moduls interessiert ist).

## <a name="return-value"></a>Rückgabewert
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.

## <a name="see-also"></a>Weitere Informationen
- [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)
