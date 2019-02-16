---
title: GUID_ARRAY | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- GUID_ARRAY structure
ms.assetid: 9e12500c-2c1c-49b1-a0ba-e08366c97eb8
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c3aa33d8cef230d07c9b5f7cd3bd11a538fa651a
ms.sourcegitcommit: 752f03977f45169585e407ef719450dbe219b7fc
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/15/2019
ms.locfileid: "56315520"
---
# <a name="guidarray"></a>GUID_ARRAY
Ein Array von eindeutigen Bezeichnern für verfügbare Debug-Engines beschreibt.

## <a name="syntax"></a>Syntax

```cpp
typedef struct tagGUID_ARRAY
{
    DWORD dwCount;
    GUID *Members;
} GUID_ARRAY;
```

```csharp
public struct GUID_ARRAY
{
    public uint dwCount;
    public Guid Members;
}
```

## <a name="terms"></a>Begriffe
dwCount  
Die Anzahl von eindeutigen Bezeichnern im Array.

Member  
Array, das eindeutige Bezeichner enthält.

## <a name="remarks"></a>Hinweise
Diese Struktur wird zurückgegeben, durch die [GetEngineFilter](../../../extensibility/debugger/reference/idebugprocess3-getenginefilter.md) Methode.

## <a name="requirements"></a>Anforderungen
Header: Msdbg.h

Namespace: Microsoft.VisualStudio.Debugger.Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Siehe auch
[Strukturen und Unions](../../../extensibility/debugger/reference/structures-and-unions.md)  
[GetEngineFilter](../../../extensibility/debugger/reference/idebugprocess3-getenginefilter.md)
