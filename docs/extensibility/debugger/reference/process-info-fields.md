---
title: PROCESS_INFO_FIELDS | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- PROCESS_INFO_FIELDS
helpviewer_keywords:
- PROCESS_INFO_FIELDS enumeration
ms.assetid: 0d9cc345-3d3a-44d8-ae15-a67acb97a828
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: f81709e7146bbdef13daa3564bb784fd9c08d58e
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80714015"
---
# <a name="process_info_fields"></a>PROCESS_INFO_FIELDS
Es wurde angegeben, welche Art von Informationen für einen Prozess abgerufen werden sollen.

## <a name="syntax"></a>Syntax

```cpp
enum enum_PROCESS_INFO_FIELDS { 
   PIF_FILE_NAME             = 0x00000001,
   PIF_BASE_NAME             = 0x00000002,
   PIF_TITLE                 = 0x00000004,
   PIF_PROCESS_ID            = 0x00000008,
   PIF_SESSION_ID            = 0x00000010,
   PIF_ATTACHED_SESSION_NAME = 0x00000020,
   PIF_CREATION_TIME         = 0x00000040,
   PIF_FLAGS                 = 0x00000080,
   PIF_ALL                   = 0x000000ff
};
typedef DWORD PROCESS_INFO_FIELDS;
```

```csharp
public enum enum_PROCESS_INFO_FIELDS { 
   PIF_FILE_NAME             = 0x00000001,
   PIF_BASE_NAME             = 0x00000002,
   PIF_TITLE                 = 0x00000004,
   PIF_PROCESS_ID            = 0x00000008,
   PIF_SESSION_ID            = 0x00000010,
   PIF_ATTACHED_SESSION_NAME = 0x00000020,
   PIF_CREATION_TIME         = 0x00000040,
   PIF_FLAGS                 = 0x00000080,
   PIF_ALL                   = 0x000000ff
};
```

## <a name="fields"></a>Felder
 `PIF_FILE_NAME`\
 Initialisieren/verwenden `bstrFileName` Sie das Feld der [PROCESS_INFO](../../../extensibility/debugger/reference/process-info.md) Struktur.

 `PIF_BASE_NAME`\
 Initialisieren/verwenden `bstrBaseName` Sie das `PROCESS_INFO` Feld der Struktur.

 `PIF_TITLE`\
 Initialisieren/verwenden `bstrTitle` Sie das `PROCESS_INFO` Feld der Struktur.

 `PIF_PROCESS_ID`\
 Initialisieren/verwenden `ProcessId` Sie das `PROCESS_INFO` Feld der Struktur.

 `PIF_SESSION_ID`\
 Initialisieren/verwenden `dwSessionId` Sie das `PROCESS_INFO` Feld der Struktur.

 `PIF_ATTACHED_SESSION_NAME`\
 Initialisieren/verwenden `bstrAttachedSessionName` Sie das `PROCESS_INFO` Feld der Struktur.

 `PIF_CREATION_TIME`\
 Initialisieren/verwenden `CreationTime` Sie das `PROCESS_INFO` Feld der Struktur.

 `PIF_FLAGS`\
 Initialisieren/verwenden `Flags` Sie das `PROCESS_INFO` Feld der Struktur.

 `PIF_ALL`\
 Füllt alle Felder aus.

## <a name="remarks"></a>Bemerkungen
 An die [GetInfo-Methode](../../../extensibility/debugger/reference/idebugprocess2-getinfo.md) übergeben, um anzugeben, welche Felder der [PROCESS_INFO-Struktur](../../../extensibility/debugger/reference/process-info.md) initialisiert werden sollen.

 Wird auch `Fields` im `PROCESS_INFO` Feld der Struktur verwendet, um anzugeben, welche Felder verwendet und gültig sind.

 Diese Flags können mit einem `OR`bitwise kombiniert werden.

## <a name="requirements"></a>Requirements (Anforderungen)
 Kopfzeile: msdbg.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Weitere Informationen
- [Enumerationen](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [PROCESS_INFO](../../../extensibility/debugger/reference/process-info.md)
