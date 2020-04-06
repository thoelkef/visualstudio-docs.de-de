---
title: IDebugProgram2::EnumCodeContexts | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgram2::EnumCodeContexts
helpviewer_keywords:
- IDebugProgram2::EnumCodeContexts
ms.assetid: 478e06a2-07bb-4841-8887-deab0f42ebd0
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: c22a5ce398e76ee97b2f0448900fd4e38f996615
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80723048"
---
# <a name="idebugprogram2enumcodecontexts"></a>IDebugProgram2::EnumCodeContexts
Ruft eine Liste der Codekontexte für eine bestimmte Position in einer Quelldatei ab.

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

## <a name="parameters"></a>Parameter
`pDocPos`\
[in] Ein [IDebugDocumentPosition2-Objekt,](../../../extensibility/debugger/reference/idebugdocumentposition2.md) das eine abstrakte Position in einer Quelldatei darstellt, die der IDE bekannt ist.

`ppEnum`[out] Gibt ein [IEnumDebugCodeContexts2-Objekt](../../../extensibility/debugger/reference/ienumdebugcodecontexts2.md) zurück, das eine Liste der Codekontexte enthält.

## <a name="return-value"></a>Rückgabewert
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Bemerkungen
 Mit dieser Methode kann der Session-Debug-Manager (SDM) oder die IDE eine Quelldateiposition einer Codeposition zuordnen. Mehr als ein Codekontext wird zurückgegeben, wenn die Quelle mehrere Codeblöcke generiert (z. B. C++-Vorlagen).

## <a name="see-also"></a>Weitere Informationen
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [IDebugDocumentPosition2](../../../extensibility/debugger/reference/idebugdocumentposition2.md)
- [IEnumDebugCodeContexts2](../../../extensibility/debugger/reference/ienumdebugcodecontexts2.md)
