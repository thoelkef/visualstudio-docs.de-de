---
title: IDebugDocument2::GetDocumentClassID | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDocument2::GetDocumentClassID
helpviewer_keywords:
- IDebugDocument2::GetDocumentClassID
ms.assetid: 111c2b85-ebfa-487f-b896-2ec4a3eac4d1
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9e969d7c6f17aeaa8642b9988e741318ec1591d6
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/22/2019
ms.locfileid: "56691253"
---
# <a name="idebugdocument2getdocumentclassid"></a>IDebugDocument2::GetDocumentClassID
Ruft die Klassen-ID des Dokuments ab.

## <a name="syntax"></a>Syntax

```cpp
HRESULT GetDocumentClassID( 
   CLSID* pclsid
);
```

```csharp
int GetDocumentClassID( 
   out Guid pclsid
);
```

#### <a name="parameters"></a>Parameter
 `pclsid`

 [out] Gibt eine GUID, die Klassen-ID des Dokuments zurück.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird `S_OK`ist, andernfalls ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Hinweise
 Die Klassen-GUID kann verwendet werden, um einzelne Klassen zu instanziieren, von die jeder ein Dokument darstellt.

## <a name="see-also"></a>Siehe auch
- [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md)