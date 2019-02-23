---
title: IDebugProgram2::EnumCodeContexts | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgram2::EnumCodeContexts
helpviewer_keywords:
- IDebugProgram2::EnumCodeContexts
ms.assetid: 478e06a2-07bb-4841-8887-deab0f42ebd0
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 77d92a65b77cbec94a6c74852393627af6763bad
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/22/2019
ms.locfileid: "56685390"
---
# <a name="idebugprogram2enumcodecontexts"></a>IDebugProgram2::EnumCodeContexts
Ruft eine Liste der Codekontexte für eine bestimmte Position in einer Quelldatei.

## <a name="syntax"></a>Syntax

```cpp
HRESULT EnumCodeContexts( 
   IDebugDocumentPosition2*  pDocPos,
   IEnumDebugCodeContexts2** ppEnum
);
```

```csharp
int EnumCodeContexts( 
   IDebugDocumentPosition2     pDocPos,
   out IEnumDebugCodeContexts2 ppEnum
);
```

#### <a name="parameters"></a>Parameter
 `pDocPos`

 [in] Ein [IDebugDocumentPosition2](../../../extensibility/debugger/reference/idebugdocumentposition2.md) Objekt, das eine abstrakte Position in einer Quelldatei bekannt, dass die IDE darstellt.

 `ppEnum`

 [out] Gibt eine [IEnumDebugCodeContexts2](../../../extensibility/debugger/reference/ienumdebugcodecontexts2.md) -Objekt, das eine Liste der Codekontexte enthält.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird `S_OK`ist, andernfalls ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Hinweise
 Mit dieser Methode können die Sitzung-Debug-Manager (SDM) oder eine IDE, um eine Quelle Dateiposition an einer Position Code zuzuordnen. Mehr als einem Codekontext wird zurückgegeben, wenn die Quelle mehrere Blöcke von Code (z. B. C++-Vorlagen) generiert.

## <a name="see-also"></a>Siehe auch
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [IDebugDocumentPosition2](../../../extensibility/debugger/reference/idebugdocumentposition2.md)
- [IEnumDebugCodeContexts2](../../../extensibility/debugger/reference/ienumdebugcodecontexts2.md)