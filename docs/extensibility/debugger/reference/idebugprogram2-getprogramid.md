---
title: 'IDebugProgram2:: getProgramId | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgram2::GetProgramId
helpviewer_keywords:
- IDebugProgram2::GetProgramId
ms.assetid: 2c31c0aa-2b71-46c7-849c-356e237d26f8
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 8bb172f48b63ef2ec182f1a83d599a91eff1e2ac
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "80722777"
---
# <a name="idebugprogram2getprogramid"></a>IDebugProgram2::GetProgramId
Ruft eine GUID für dieses Programm ab.

## <a name="syntax"></a>Syntax

```cpp
HRESULT GetProgramId( 
   GUID* pguidProgramId
);
```

```csharp
int GetProgramId( 
   out Guid pguidProgramId
);
```

## <a name="parameters"></a>Parameter
`pguidProgramId`\
vorgenommen Gibt die `GUID` für dieses Programm zurück.

## <a name="return-value"></a>Rückgabewert
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Bemerkungen
 Eine Debug-Engine (de) muss den Programm Bezeichner zurückgeben, der ursprünglich an die [onattach](../../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md) -oder [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md) -Methode übermittelt wurde Dies ermöglicht die Identifizierung des Programms in Debugger-Komponenten.

## <a name="see-also"></a>Weitere Informationen
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [OnAttach](../../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md)
- [Anfügen](../../../extensibility/debugger/reference/idebugengine2-attach.md)
