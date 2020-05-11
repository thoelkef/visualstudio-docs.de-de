---
title: GETNAME_TYPE | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- GETNAME_TYPE
helpviewer_keywords:
- GETNAME_TYPE enumeration
ms.assetid: 2f9f1679-e9e8-4c9c-ac90-aa07bfe69914
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 1d0d146ec4ed7340bde36b298df9d455257b35fe
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80736675"
---
# <a name="getname_type"></a>GETNAME_TYPE
Gibt den Namenstyp der abzurufenden Dateien an.

## <a name="syntax"></a>Syntax

```cpp
enum enum_GETNAME_TYPE {
    GN_NAME         = 0,
    GN_FILENAME     = 1,
    GN_BASENAME     = 2,
    GN_MONIKERNAME  = 3,
    GN_URL          = 4,
    GN_TITLE        = 5,
    GN_STARTPAGEURL = 6
};
typedef DWORD GETNAME_TYPE;
```

```csharp
public enum enum_GETNAME_TYPE {
    GN_NAME         = 0,
    GN_FILENAME     = 1,
    GN_BASENAME     = 2,
    GN_MONIKERNAME  = 3,
    GN_URL          = 4,
    GN_TITLE        = 5,
    GN_STARTPAGEURL = 6
};
```

## <a name="fields"></a>Felder
`GN_NAME`\
Gibt einen Anzeigenamen des Dokuments oder Kontexts an.

`GN_FILENAME`\
Gibt den vollständigen Pfad des Dokuments oder Kontexts an.

`GN_BASENAME`\
Gibt einen Basisdateinamen anstelle eines vollständigen Pfads des Dokuments oder Kontexts an.

`GN_MONIKERNAME`\
Gibt einen eindeutigen Namen des Dokuments oder Kontexts in Form eines Monikers an.

`GN_URL`\
Gibt einen URL-Namen des Dokuments oder Kontexts an.

`GN_TITLE`\
Gibt einen Titel des Dokuments an, sofern vorhanden.

`GN_STARTPAGEURL`\
Ruft die URL der Startseite für Prozesse ab.

## <a name="remarks"></a>Bemerkungen
Diese Werte werden als Parameter an die [GetName-,](../../../extensibility/debugger/reference/idebugdocument2-getname.md) [GetName-](../../../extensibility/debugger/reference/idebugdocumentcontext2-getname.md)und [GetName-Methoden](../../../extensibility/debugger/reference/idebugprocess2-getname.md) übergeben, um anzugeben, welche Art von Name zurückgegeben werden soll.

## <a name="requirements"></a>Requirements (Anforderungen)
Kopfzeile: msdbg.h

Namespace: Microsoft.VisualStudio.Debugger.Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Weitere Informationen
- [Enumerationen](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [GetName](../../../extensibility/debugger/reference/idebugdocument2-getname.md)
- [GetName](../../../extensibility/debugger/reference/idebugdocumentcontext2-getname.md)
- [GetName](../../../extensibility/debugger/reference/idebugprocess2-getname.md)
