---
title: IDebugActivateDocumentEvent2::GetDocument | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugActivateDocumentEvent2::GetDocument
helpviewer_keywords:
- GetDocument method
- IDebugActivateDocumentEvent2::GetDocument method
ms.assetid: b3c32f1b-f3de-409d-920d-ba7b3fa84fcd
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 1ba06a44f24a6cd33c42b82bdf39aa4e4dfd799a
ms.sourcegitcommit: 77b4ca625674658d5c5766e684fa0e2a07cad4da
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/14/2019
ms.locfileid: "65615306"
---
# <a name="idebugactivatedocumentevent2getdocument"></a>IDebugActivateDocumentEvent2::GetDocument
Ruft das Dokument zu aktivieren.

## <a name="syntax"></a>Syntax

```cpp
HRESULT GetDocument ( 
   IDebugDocument2** ppDoc
);
```

```csharp
int GetDocument ( 
   out IDebugDocument2 ppDoc
);
```

## <a name="parameters"></a>Parameter
`ppDoc`\
[out] Gibt eine [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md) -Objekt, das Dokument zu aktivierenden darstellt.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird `S_OK`ist, andernfalls ein Fehlercode zurückgegeben.

## <a name="see-also"></a>Siehe auch
- [IDebugActivateDocumentEvent2](../../../extensibility/debugger/reference/idebugactivatedocumentevent2.md)
- [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md)