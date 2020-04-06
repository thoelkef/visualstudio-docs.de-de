---
title: MESSAGETYPE | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- MESSAGETYPE
helpviewer_keywords:
- MESSAGETYPE enumeration
ms.assetid: 800cc77d-3c27-4763-a9df-552a9384bd49
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: b4d0fd12495a59427500c16ef6f37d9f8b6e61f5
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80714497"
---
# <a name="messagetype"></a>MESSAGETYPE
Gibt den Nachrichtentyp und den Grund an.

## <a name="syntax"></a>Syntax

```cpp
enum enum_MESSAGETYPE { 
   MT_OUTPUTSTRING      = 0x0000001,
   MT_MESSAGEBOX        = 0x00000002,
   MT_TYPE_MASK         = 0x000000FF,
   MT_REASON_EXCEPTION  = 0x00000100,
   MT_REASON_TRACEPOINT = 0x00000200,
   MT_REASON_MASK       = 0x0000FF00
};
typedef DWORD MESSAGETYPE;
```

```csharp
public enum enum_MESSAGETYPE { 
   MT_OUTPUTSTRING      = 0x0000001,
   MT_MESSAGEBOX        = 0x00000002,
   MT_TYPE_MASK         = 0x000000FF,
   MT_REASON_EXCEPTION  = 0x00000100,
   MT_REASON_TRACEPOINT = 0x00000200,
   MT_REASON_MASK       = 0x0000FF00
};
```

## <a name="fields"></a>Felder
 `MT_OUTPUTSTRING`\
 Gibt an, dass die Nachricht an das Ausgabefenster gesendet werden soll. Dies schließt sich `MT_MESSAGEBOX`gegenseitig aus.

 `MT_MESSAGEBOX`\
 Gibt an, dass die Meldung in einem Meldungsfeld angezeigt werden soll. Dies schließt sich `MT_OUTPUTSTRING`gegenseitig aus.

 `MT_TYPE_MASK`\
 Ein Maskenwert, um das Ziel für die Nachricht zu isolieren.

 `MT_REASON_EXCEPTION`\
 Gibt an, dass aufgrund einer Ausnahme ein Meldungsfeld angezeigt wird. Dies schließt sich `MT_REASON_TRACEPOINT`gegenseitig aus.

 `MT_REASON_TRACEPOINT`\
 Gibt an, dass ein Meldungsfeld angezeigt wird, wenn ein Ablaufverfolgungspunkt erreicht wird. Dies schließt sich `MT_REASON_EXCEPTION`gegenseitig aus.

 `MT_REASON_MASK`\
 Ein Maskenwert, um den Grund für die angezeigte Nachricht zu isolieren.

## <a name="remarks"></a>Bemerkungen
 Diese Werte werden von den [Methoden GetMessage](../../../extensibility/debugger/reference/idebugmessageevent2-getmessage.md) und [GetErrorMessage](../../../extensibility/debugger/reference/idebugerrorevent2-geterrormessage.md) zurückgegeben.

 Einer der Grundwerte kann mit einem der Ausgabezielwerte `OR`mit einem bitweisen kombiniert werden.

## <a name="requirements"></a>Requirements (Anforderungen)
 Kopfzeile: msdbg.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Weitere Informationen
- [Enumerationen](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [GetMessage](../../../extensibility/debugger/reference/idebugmessageevent2-getmessage.md)
- [GetErrorMessage](../../../extensibility/debugger/reference/idebugerrorevent2-geterrormessage.md)
