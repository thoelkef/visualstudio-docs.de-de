---
title: 'IDebugProgramNode2:: getengineingefo | Microsoft-Dokumentation'
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "80722100"
---
# <a name="idebugprogramnode2getengineinfo"></a>IDebugProgramNode2::GetEngineInfo
Ruft den Namen und den Bezeichner der Debug-Engine (de) ab, die ein Programm ausgeführt wird.

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
vorgenommen Gibt den Namen des Programms zurück, auf dem das Programm ausgeführt wird (C++-specific: Dies kann ein NULL-Zeiger sein, der angibt, dass der Aufrufer nicht an dem Namen der Engine interessiert ist).

`pguidEngine`\
vorgenommen Gibt die Globally Unique Identifier der de zurück, die das Programm ausgeführt hat (C++-specific: Dies kann ein NULL-Zeiger sein, der angibt, dass der Aufrufer nicht an der GUID der Engine interessiert ist).

## <a name="return-value"></a>Rückgabewert
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.

## <a name="see-also"></a>Weitere Informationen
- [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)
