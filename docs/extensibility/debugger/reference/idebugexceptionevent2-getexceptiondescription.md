---
title: IDebugExceptionEvent2::GetExceptionDescription | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugExceptionEvent2::GetExceptionDescription
helpviewer_keywords:
- IDebugExceptionEvent2::GetExceptionDescription
ms.assetid: d07d458f-5729-47e4-9b77-1bd59c61a75a
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 732ca932179cee48a3395e6cdb765c244f007d0f
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/22/2019
ms.locfileid: "56680138"
---
# <a name="idebugexceptionevent2getexceptiondescription"></a>IDebugExceptionEvent2::GetExceptionDescription
Ruft eine anzeigbare Beschreibung der Ausnahme ab.

## <a name="syntax"></a>Syntax

```cpp
HRESULT GetExceptionDescription( 
   BSTR* pbstrDescription
);
```

```csharp
int GetExceptionDescription( 
   out string pbstrDescription
);
```

#### <a name="parameters"></a>Parameter
 `pbstrDescription`

 [out] Gibt eine anzeigbare Beschreibung der Ausnahme zurück.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird `S_OK`ist, andernfalls ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Hinweise
 Die von dieser Methode zurückgegebene Zeichenfolge ist üblicherweise der Name der Ausnahme, und sehen Sie in der **Ausgabe** Fenster beim Auftreten der Ausnahme.

## <a name="see-also"></a>Siehe auch
- [IDebugExceptionEvent2](../../../extensibility/debugger/reference/idebugexceptionevent2.md)