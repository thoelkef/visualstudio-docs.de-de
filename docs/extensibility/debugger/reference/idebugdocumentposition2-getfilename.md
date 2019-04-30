---
title: IDebugDocumentPosition2::GetFileName | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDocumentPosition2::GetFileName
helpviewer_keywords:
- IDebugDocumentPosition2::GetFileName
ms.assetid: d713635e-088f-465b-b26d-00ac971c9e86
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8dc5e6ef5317e24e53215dad8f32bc95ee400762
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62921356"
---
# <a name="idebugdocumentposition2getfilename"></a>IDebugDocumentPosition2::GetFileName
Ruft den Dateinamen der Quelldatei, die die Dokumentposition enthält.

## <a name="syntax"></a>Syntax

```cpp
HRESULT GetFileName( 
   BSTR* pbstrFileName
);
```

```csharp
int GetFileName( 
   out string pbstrFileName
);
```

#### <a name="parameters"></a>Parameter
 `pbstrFileName`

 [out] Gibt den Dateinamen der Quelldatei zurück.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird `S_OK`ist, andernfalls ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Hinweise
 Eine Quelldatei nicht immer einen Dateinamen möglicherweise (die Quelldatei kann nicht auf dem Datenträger, z. B. vorhanden).

## <a name="see-also"></a>Siehe auch
- [IDebugDocumentPosition2](../../../extensibility/debugger/reference/idebugdocumentposition2.md)