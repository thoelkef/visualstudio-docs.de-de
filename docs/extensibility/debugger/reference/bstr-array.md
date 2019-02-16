---
title: BSTR_ARRAY | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- BSTR_ARRAY
helpviewer_keywords:
- BSTR_ARRAY structure
ms.assetid: 48da37f7-a237-48a9-9ff9-389c1a00862c
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 79502e4a7a42a4c83957c0ef6b470fa9753db6fd
ms.sourcegitcommit: 752f03977f45169585e407ef719450dbe219b7fc
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/15/2019
ms.locfileid: "56317457"
---
# <a name="bstrarray"></a>BSTR_ARRAY
Eine Struktur, die ein Array von Zeichenfolgen beschreibt.

## <a name="syntax"></a>Syntax

```cpp
typedef struct tagBSTR_ARRAY {
    DWORD dwCount;
    BSTR* Members;
} BSTR_ARRAY;
```

```csharp
struct BSTR_ARRAY {
    DWORD    dwCount;
    string[] Members;
}
```

## <a name="terms"></a>Begriffe
dwCount  
Anzahl der Zeichenfolgen in `Members` Array.

Member  
Array von Zeichenfolgen.

## <a name="remarks"></a>Hinweise
Diese Struktur wird zurückgegeben, die [EnumPersistedPorts](../../../extensibility/debugger/reference/idebugportsupplier3-enumpersistedports.md) Methode.

[Nur für C++] Jeder einzelnen Zeichenfolge muss freigegeben werden, mithilfe von `SysFreeString`, und die `Members` Array muss mit dem freigegeben `CoTaskMemFree`.

## <a name="requirements"></a>Anforderungen
Header: msdbg.h

Namespace: Microsoft.VisualStudio.Debugger.Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Siehe auch
[Strukturen und Unions](../../../extensibility/debugger/reference/structures-and-unions.md)  
[EnumPersistedPorts](../../../extensibility/debugger/reference/idebugportsupplier3-enumpersistedports.md)
