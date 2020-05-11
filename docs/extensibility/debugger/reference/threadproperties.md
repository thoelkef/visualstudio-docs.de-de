---
title: THREADPROPERTIES | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- THREADPROPERTIES
helpviewer_keywords:
- THREADPROPERTIES structure
ms.assetid: 7d397207-db03-4ec0-9f79-3794056ed89f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: bd0ed4e33b1f8e0e905f3c88493c9f513c177fbc
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80713424"
---
# <a name="threadproperties"></a>THREADPROPERTIES
Beschreibt die Eigenschaften eines Threads.

## <a name="syntax"></a>Syntax

```cpp
typedef struct _tagTHREADPROPERTIES { 
   THREADPROPERTY_FIELDS dwFields;
   DWORD                 dwThreadId;
   DWORD                 dwSuspendCount;
   DWORD                 dwThreadState;
   BSTR                  bstrPriority;
   BSTR                  bstrName;
   BSTR                  bstrLocation;
} THREADPROPERTIES;
```

```csharp
public struct THREADPROPERTIES { 
   public uint   dwFields;
   public uint   dwThreadId;
   public uint   dwSuspendCount;
   public uint   dwThreadState;
   public string bstrPriority;
   public string bstrName;
   public string bstrLocation;
};
```

## <a name="members"></a>Member
 `dwFields`\
 Eine Kombination von [THREADPROPERTY_FIELDS](../../../extensibility/debugger/reference/threadproperty-fields.md) Flags aus der THREADPROPERTY_FIELDS-Enumeration, die beschreibt, welche Felder in dieser Struktur gültig sind.

 `dwThreadId`\
 Die Thread-ID.

 `dwSuspendCount`\
 Die Anzahl der Thread-Aussetzen.

 `dwThreadState`\
 Ein Wert [THREADSTATE](../../../extensibility/debugger/reference/threadstate.md) aus der THREADSTATE-Enumeration, der den Status des Betriebssystemthreads angibt.

 `bstrPriority`\
 Eine Zeichenfolge, die die Threadpriorität angibt; z. B. "Über Normal", "Normal" oder "Zeitkritisch".

 `bstName`\
 Der Threadname.

 `bstrLocation`\
 Die Threadposition (in der Regel der oberste Stapelrahmen), der in der Regel als Name der Methode ausgedrückt wird, bei der die Ausführung derzeit angehalten wird.

## <a name="remarks"></a>Bemerkungen
 Diese Struktur wird durch einen Aufruf der [GetThreadProperties-Methode](../../../extensibility/debugger/reference/idebugthread2-getthreadproperties.md) ausgefüllt. Die so zurückgegebenen Informationen werden **Threads** in der Regel beim Auffüllen des Threads-Fensters verwendet.

## <a name="requirements"></a>Requirements (Anforderungen)
 Kopfzeile: msdbg.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Weitere Informationen
- [Structures and Unions](../../../extensibility/debugger/reference/structures-and-unions.md)
- [GetThreadProperties](../../../extensibility/debugger/reference/idebugthread2-getthreadproperties.md)
- [THREADPROPERTY_FIELDS](../../../extensibility/debugger/reference/threadproperty-fields.md)
- [THREADSTATE](../../../extensibility/debugger/reference/threadstate.md)
