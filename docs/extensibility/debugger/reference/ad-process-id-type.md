---
title: AD_PROCESS_ID_TYPE | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- AD_PROCESS_ID_TYPE
helpviewer_keywords:
- AD_PROCESS_ID_TYPE enumeration
ms.assetid: 0aab80e9-285a-4697-94ac-c864d42a6aaa
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: a88fbe97cede8d343f1a96bc1917a69b8905b02b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738191"
---
# <a name="ad_process_id_type"></a>AD_PROCESS_ID_TYPE
Gibt an, wie eine Prozess-ID in der [AD_PROCESS_ID-Struktur](../../../extensibility/debugger/reference/ad-process-id.md) interpretiert wird.

## <a name="syntax"></a>Syntax

```cpp
enum enum_AD_PROCESS_ID {
    AD_PROCESS_ID_SYSTEM = 0,
    AD_PROCESS_ID_GUID   = 1
};
typedef DWORD AD_PROCESS_ID_TYPE;
```

```csharp
public enum enum_AD_PROCESS_ID {
    AD_PROCESS_ID_SYSTEM = 0,
    AD_PROCESS_ID_GUID   = 1
};
```

## <a name="fields"></a>Felder
`AD_PROCESS_ID_SYSTEM`\
Die Prozess-ID ist eine Systemkennung. Verwenden `ProcessId.dwProcessId` Sie das Feld der [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md) Struktur.

`AD_PROCESS_ID_GUID`\
Prozess-ID ist eine GUID. Verwenden `ProcessId.guidProcessId` Sie das `AD_PROCESS_ID` Feld der Struktur.

## <a name="remarks"></a>Bemerkungen
Wird für `ProcessIdType` das Element der [AD_PROCESS_ID-Struktur](../../../extensibility/debugger/reference/ad-process-id.md) verwendet, um den Typ der Prozess-ID zu identifizieren, die in der Struktur enthalten ist. Bestimmt, wie `ProcessId` die Union in der Struktur interpretiert werden soll.

## <a name="requirements"></a>Requirements (Anforderungen)
Kopfzeile: msdbg.h

Namespace: Microsoft.VisualStudio.Debugger.Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Weitere Informationen
- [Enumerationen](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md)
