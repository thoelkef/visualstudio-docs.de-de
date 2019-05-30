---
title: IEEVisualizerService::GetValueDisplayStringCount | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IEEVisualizerService::GetValueDisplayStringCount
- GetValueDisplayStringCount
ms.assetid: d683a833-fbfb-4042-84df-6905124a268a
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 20e09dad1d87df646d1dc8ef7509842b49a8cdaa
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/29/2019
ms.locfileid: "66308924"
---
# <a name="ieevisualizerservicegetvaluedisplaystringcount"></a>IEEVisualizerService::GetValueDisplayStringCount
Ruft die Anzahl der Zeichenfolgen, die für die angegebene Eigenschaft oder das Feld angezeigt.

## <a name="syntax"></a>Syntax

```cpp
HRESULT GetValueDisplayStringCount (
   DWORD         displayKind,
   IDebugField * propertyOrField,
   ULONG *       pcelt
);
```

```csharp
int GetValueDisplayStringCount (
   uint        displayKind,
   IDebugField propertyOrField,
   out ulong   pcelt
);
```

## <a name="parameters"></a>Parameter
`displayKind`\
[in] Wert aus der [DisplayKind](../../../extensibility/debugger/reference/displaykind.md) Enumeration.

`propertyOrField`\
[in] Ein [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) Schnittstelle, die eine Eigenschaft oder ein Feld darstellt.

`pcelt`\
[out] Gibt die Anzahl der anzuzeigenden Zeichenfolgen zurück.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird `S_OK`ist, andernfalls ein Fehlercode zurückgegeben.

## <a name="see-also"></a>Siehe auch
- [IEEVisualizerService](../../../extensibility/debugger/reference/ieevisualizerservice.md)