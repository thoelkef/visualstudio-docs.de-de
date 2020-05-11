---
title: PROCESS_INFO | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- PROCESS_INFO
helpviewer_keywords:
- PROCESS_INFO structure
ms.assetid: 260c33cc-a05e-4645-84b6-536d0b3b0537
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: ef73145fb0a2598dc5e4ee98e8652314e0bc1c89
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80713885"
---
# <a name="process_info"></a>PROCESS_INFO
Enthält Informationen zu einem Prozess.

## <a name="syntax"></a>Syntax

```cpp
typedef struct tagPROCESS_INFO { 
   PROCESS_INFO_FIELDS Fields;
   BSTR                bstrFileName;
   BSTR                bstrBaseName;
   BSTR                bstrTitle;
   AD_PROCESS_ID       ProcessId;
   DWORD               dwSessionId;
   BSTR                bstrAttachedSessionName;
   FILETIME            CreationTime;
   PROCESS_INFO_FLAGS  Flags;
} PROCESS_INFO;
```

```csharp
public struct PROCESS_INFO { 
   public uint          Fields;
   public string        bstrFileName;
   public string        bstrBaseName;
   public string        bstrTitle;
   public AD_PROCESS_ID ProcessId;
   public uint          dwSessionId;
   public string        bstrAttachedSessionName;
   public FILETIME      CreationTime;
   public uint          Flags;
};
```

## <a name="members"></a>Member
 `Fields`\
 Eine Kombination von [PROCESS_INFO_FIELDS](../../../extensibility/debugger/reference/process-info-fields.md) Flags aus der PROCESS_INFO_FIELDS-Enumeration, die angeben, welche Felder ausgefüllt werden.

 `bstrFileName`\
 Der vollständige Pfadname des Prozesses. Entspricht dem Aufrufen der [GetName-Methode](../../../extensibility/debugger/reference/idebugprocess2-getname.md) mit dem Parameter `GN_FILENAME`.

 `bstrBaseName`\
 Der Dateiname und die Erweiterung des Prozesses. Entspricht dem `IDebugProcess2::Getname` Aufruf der `GN_BASENAME`Methode mit dem Parameter .

 `bstrTitle`\
 Der Titel des Prozesses, sofern vorhanden. Entspricht dem `IDebugProcess2::Getname` Aufruf der `GN_TITLE`Methode mit dem Parameter .

 `ProcessId`\
 Die [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md) Struktur, die den Prozess identifiziert. Entspricht dem Aufrufen der [GetPhysicalProcessId-Methode.](../../../extensibility/debugger/reference/idebugprocess2-getphysicalprocessid.md)

 `dwSessionId`\
 Der Bezeichner der Debugsitzung, in der dieser Prozess ausgeführt wird.

 `bstrAttachedSessionName`\
 Der angehängte Sitzungsname. Entspricht dem Aufrufen der [GetAttachedSessionName-Methode.](../../../extensibility/debugger/reference/idebugprocess2-getattachedsessionname.md)

 `CreationTime`\
 Der Zeitpunkt, zu dem der Prozess erstellt wurde.

 `Flags`\
 Eine Kombination von [PROCESS_INFO_FLAGS](../../../extensibility/debugger/reference/process-info-flags.md) Flags aus der PROCESS_INFO_FLAGS-Enumeration, die Eigenschaften des Prozesses angeben.

## <a name="remarks"></a>Bemerkungen
 Diese Struktur wird an die [GetInfo-Methode](../../../extensibility/debugger/reference/idebugprocess2-getinfo.md) übergeben, bei der sie ausgefüllt wird.

## <a name="requirements"></a>Requirements (Anforderungen)
 Kopfzeile: msdbg.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Weitere Informationen
- [Structures and Unions](../../../extensibility/debugger/reference/structures-and-unions.md)
- [PROCESS_INFO_FIELDS](../../../extensibility/debugger/reference/process-info-fields.md)
- [PROCESS_INFO_FLAGS](../../../extensibility/debugger/reference/process-info-flags.md)
- [GetInfo](../../../extensibility/debugger/reference/idebugprocess2-getinfo.md)
- [GetName](../../../extensibility/debugger/reference/idebugprocess2-getname.md)
- [GetPhysicalProcessId](../../../extensibility/debugger/reference/idebugprocess2-getphysicalprocessid.md)
- [GetAttachedSessionName](../../../extensibility/debugger/reference/idebugprocess2-getattachedsessionname.md)
