---
title: MESSAGETYPE | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- MESSAGETYPE
helpviewer_keywords:
- MESSAGETYPE enumeration
ms.assetid: 800cc77d-3c27-4763-a9df-552a9384bd49
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 7f3485aa2e5650345c0b14c6cb8093034043285a
ms.sourcegitcommit: 50f0c3f2763a05de8482b3579026d9c76c0e226c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/09/2019
ms.locfileid: "65461013"
---
# <a name="messagetype"></a>MESSAGETYPE
Gibt den Nachrichtentyp und dem Grund.

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
 Gibt an, dass die Meldung im Ausgabefenster gesendet werden soll. Dies ist von sich gegenseitig ausschließende `MT_MESSAGEBOX`.

 `MT_MESSAGEBOX`\
 Gibt an, dass die Nachricht in einem Meldungsfeld angezeigt werden soll. Dies ist von sich gegenseitig ausschließende `MT_OUTPUTSTRING`.

 `MT_TYPE_MASK`\
 Ein-Wert, das Ziel für die Nachricht zu isolieren.

 `MT_REASON_EXCEPTION`\
 Gibt an, dass als Ergebnis einer Ausnahme ein Meldungsfeld angezeigt wird. Dies ist von sich gegenseitig ausschließende `MT_REASON_TRACEPOINT`.

 `MT_REASON_TRACEPOINT`\
 Gibt an, dass als Ergebnis einen Ablaufverfolgungspunkt erreicht ein Meldungsfeld angezeigt wird. Dies ist an sich gegenseitig ausschließende `MT_REASON_EXCEPTION`.

 `MT_REASON_MASK`\
 Ein-Wert, den Grund für die anzuzeigende Nachricht zu isolieren.

## <a name="remarks"></a>Hinweise
 Diese Werte werden zurückgegeben, aus der ["GetMessage"](../../../extensibility/debugger/reference/idebugmessageevent2-getmessage.md) und [GetErrorMessage](../../../extensibility/debugger/reference/idebugerrorevent2-geterrormessage.md) Methoden.

 Der Grund-Werte kann kombiniert werden, mit einem der die Ziel-Ausgabewerte, die mit einer bitweisen `OR`.

## <a name="requirements"></a>Anforderungen
 Header: msdbg.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Siehe auch
- [Enumerationen](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [GetMessage](../../../extensibility/debugger/reference/idebugmessageevent2-getmessage.md)
- [GetErrorMessage](../../../extensibility/debugger/reference/idebugerrorevent2-geterrormessage.md)