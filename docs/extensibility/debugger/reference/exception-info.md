---
title: EXCEPTION_INFO | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- EXCEPTION_INFO
helpviewer_keywords:
- EXCEPTION_INFO structure
ms.assetid: d046957a-b97d-420b-b46b-c67cbaef709e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: a305d34123d02b1fdbd545a438db4461643ed185
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80737021"
---
# <a name="exception_info"></a>EXCEPTION_INFO
Beschreibt einen Ausnahme- oder Laufzeitfehler, der vom zu debuggenden Programm ausgelöst wird.

## <a name="syntax"></a>Syntax

```cpp
typedef struct tagEXCEPTION_INFO {
    IDebugProgram2* pProgram;
    BSTR            bstrProgramName;
    BSTR            bstrExceptionName;
    DWORD           dwCode;
    EXCEPTION_STATE dwState;
    GUID            guidType;
} EXCEPTION_INFO;
```

```csharp
public struct EXCEPTION_INFO {
    public IDebugProgram2 pProgram;
    public string         bstrProgramName;
    public string         bstrExceptionName;
    public uint           dwCode;
    public uint           dwState;
    public Guid           guidType;
};
```

## <a name="members"></a>Member
`pProgram`\
Das [IDebugProgram2-Objekt,](../../../extensibility/debugger/reference/idebugprogram2.md) das das Programm darstellt, in dem die Ausnahme aufgetreten ist.

`bstrProgramName`\
Der Name des Programms, in dem die Ausnahme aufgetreten ist.

`bstrExceptionName`\
Der Name der Ausnahme.

`dwCode`\
Der Identifikationscode für den Ausnahme- oder Laufzeitfehler.

`dwState`\
Ein Wert [EXCEPTION_STATE](../../../extensibility/debugger/reference/exception-state.md) aus der EXCEPTION_STATE-Enumeration, die den Status der Ausnahme definiert.

`guidType`\
Der GUID-Sprachbezeichner, entweder `guidLang` oder `guidEng`.

## <a name="remarks"></a>Bemerkungen
Diese Struktur wird als Parameter an die [SetException-](../../../extensibility/debugger/reference/idebugengine2-setexception.md) und die [RemoveSetException-Methoden](../../../extensibility/debugger/reference/idebugengine2-removesetexception.md) übergeben. Diese Struktur wird auch an die [GetException-Methode](../../../extensibility/debugger/reference/idebugexceptionevent2-getexception.md) übergeben, die ausgefüllt werden soll.

## <a name="requirements"></a>Requirements (Anforderungen)
Kopfzeile: msdbg.h

Namespace: Microsoft.VisualStudio.Debugger.Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Weitere Informationen
- [Structures and Unions](../../../extensibility/debugger/reference/structures-and-unions.md)
- [EXCEPTION_STATE](../../../extensibility/debugger/reference/exception-state.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [SetException](../../../extensibility/debugger/reference/idebugengine2-setexception.md)
- [RemoveSetException](../../../extensibility/debugger/reference/idebugengine2-removesetexception.md)
- [GetException](../../../extensibility/debugger/reference/idebugexceptionevent2-getexception.md)
