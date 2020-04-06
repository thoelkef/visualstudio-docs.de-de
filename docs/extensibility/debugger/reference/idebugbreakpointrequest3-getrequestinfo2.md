---
title: IDebugBreakpointRequest3::GetRequestInfo2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBreakpointRequest3::GetRequestInfo2
helpviewer_keywords:
- IDebugBreakpointRequest3::GetRequestInfo2
ms.assetid: 33942e4a-0a0a-49e8-a693-004954f6d38a
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: f5febf664da9cd69dbd88b70056d9eac953bf581
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80734833"
---
# <a name="idebugbreakpointrequest3getrequestinfo2"></a>IDebugBreakpointRequest3::GetRequestInfo2
Diese Methode ruft die Haltepunktanforderungsinformationen ab, die diese Haltepunktanforderung beschreiben.

## <a name="syntax"></a>Syntax

```cpp
HRESULT GetRequestInfo2(
   BPREQI_FIELDS      dwFields,
   BP_REQUEST_INFO2*  bBPRequestInfo
);
```

```csharp
int GetRequestInfo2(
   enum_BPREQI_FIELDS  dwFields,
   BP_REQUEST_INFO2[]  bBPRequestInfo
);
```

## <a name="parameters"></a>Parameter
`dwFields`\
[in] Eine Kombination von Flags aus der BPREQI_FIELDS-Enumeration, die bestimmen, welche [BPREQI_FIELDS](../../../extensibility/debugger/reference/bpreqi-fields.md) `pBPRequestInfo` Felder ausgefüllt werden sollen.

`bBPRequestInfo`\
[out] Die [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md) Struktur auszufüllen.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, `S_OK`kehrt zurück; Andernfalls wird Fehlercode zurückgegeben.

## <a name="remarks"></a>Bemerkungen
 Diese Anforderung enthält mehr Informationen, als von der [GetRequestInfo-Methode](../../../extensibility/debugger/reference/idebugbreakpointrequest2-getrequestinfo.md) zurückgegeben wird.

## <a name="see-also"></a>Weitere Informationen
- [IDebugBreakpointRequest3](../../../extensibility/debugger/reference/idebugbreakpointrequest3.md)
- [GetRequestInfo](../../../extensibility/debugger/reference/idebugbreakpointrequest2-getrequestinfo.md)
- [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md)
- [BPREQI_FIELDS](../../../extensibility/debugger/reference/bpreqi-fields.md)
