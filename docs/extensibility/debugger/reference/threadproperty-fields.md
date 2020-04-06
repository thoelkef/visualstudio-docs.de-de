---
title: THREADPROPERTY_FIELDS | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- THREADPROPERTY_FIELDS
helpviewer_keywords:
- THREADPROPERTY_FIELDS enumeration
ms.assetid: 5b88acb9-03ea-4c29-a788-f0087dccbe23
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: b31c43187d1136f7a194c42749c430de6cd064a0
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80713395"
---
# <a name="threadproperty_fields"></a>THREADPROPERTY_FIELDS
Gibt an, welche Informationen zu einem Thread abgerufen werden sollen.

## <a name="syntax"></a>Syntax

```cpp
enum enum_THREADPROPERTY_FIELDS { 
   TPF_ID           = 0x0001,
   TPF_SUSPENDCOUNT = 0x0002,
   TPF_STATE        = 0x0004,
   TPF_PRIORITY     = 0x0008,
   TPF_NAME         = 0x0010,
   TPF_LOCATION     = 0x0020,
   TPF_ALLFIELDS    = 0xffffffff
};
typedef DWORD THREADPROPERTY_FIELDS;
```

```csharp
public enum enum_THREADPROPERTY_FIELDS { 
   TPF_ID           = 0x0001,
   TPF_SUSPENDCOUNT = 0x0002,
   TPF_STATE        = 0x0004,
   TPF_PRIORITY     = 0x0008,
   TPF_NAME         = 0x0010,
   TPF_LOCATION     = 0x0020,
   TPF_ALLFIELDS    = 0xffffffff
};
```

## <a name="fields"></a>Felder
 `TPF_ID`\
 Initialisieren/verwenden `dwThreadId` Sie das Feld der [THREADPROPERTIES-Struktur.](../../../extensibility/debugger/reference/threadproperties.md)

 `TPF_SUSPENDCOUNT`\
 Initialisieren/verwenden `dwSuspendCount` Sie das `THREADPROPERTIE`Feld der S-Struktur.

 `TPF_STATE`\
 Initialisieren/verwenden `dwThreadState` Sie das `THREADPROPERTIE`Feld der S-Struktur.

 `TPF_PRIORITY`\
 Initialisieren/verwenden `bstrPriority` Sie das `THREADPROPERTIE`Feld der S-Struktur.

 `TPF_NAME`\
 Initialisieren/verwenden `bstrName` Sie das `THREADPROPERTIE`Feld der S-Struktur.

 `TPF_LOCATION`\
 Initialisieren/verwenden `bstrLocation` Sie das `THREADPROPERTIE`Feld der S-Struktur.

 `TPF_ALLFIELDS`\
 Gibt alle Felder an.

## <a name="remarks"></a>Bemerkungen
 Diese Werte werden als Argument an die [GetThreadProperties-Methode](../../../extensibility/debugger/reference/idebugthread2-getthreadproperties.md) übergeben, um anzugeben, welche Felder der [THREADPROPERTIES-Struktur](../../../extensibility/debugger/reference/threadproperties.md) initialisiert werden sollen.

 Diese Werte werden `dwFields` auch in `THREADPROPERTIES` Member der Struktur verwendet, um anzugeben, welche Felder verwendet und gültig sind.

 Diese Flags können mit einem `OR`bitwise kombiniert werden.

## <a name="requirements"></a>Requirements (Anforderungen)
 Kopfzeile: msdbg.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Weitere Informationen
- [Enumerationen](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [THREADPROPERTIES](../../../extensibility/debugger/reference/threadproperties.md)
- [GetThreadProperties](../../../extensibility/debugger/reference/idebugthread2-getthreadproperties.md)
