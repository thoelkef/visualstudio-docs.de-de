---
title: TEXT_DOC_ATTR_2 | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- TEXT_DOC_ATTR_2
helpviewer_keywords:
- TEXT_DOC_ATTR_2 enumeration
ms.assetid: 2333b33b-042b-4ac6-9ebe-e66f95f52f51
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 86dc1e002c4d33ed0ef64abd707ca11f2d1fc492
ms.sourcegitcommit: 50f0c3f2763a05de8482b3579026d9c76c0e226c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/09/2019
ms.locfileid: "65460668"
---
# <a name="textdocattr2"></a>TEXT_DOC_ATTR_2
Beschreibt die Attribute eines Dokuments.

## <a name="syntax"></a>Syntax

```cpp
typedef DWORD TEXT_DOC_ATTR_2;
const TEXT_DOC_ATTR_2 TEXT_DOC_ATTR_READONLY_2 = 0x00000001;
```

```csharp
public const uint TEXT_DOC_ATTR_READONLY_2 = 0x00000001;
```

## <a name="members"></a>Member
 `TEXT_DOC_ATTR_READONLY_2`\
 Gibt an, dass das Dokument schreibgeschützt ist.

## <a name="remarks"></a>Hinweise

> [!NOTE]
> Dieser Wert ist nicht tatsächlich in der Assembly für C#-Code definiert. Stattdessen müssen Sie die Definition Ihrer Quelldatei kopieren.

 Übergeben als Argument an die [OnUpdateDocumentAttributes](../../../extensibility/debugger/reference/idebugdocumenttextevents2-onupdatedocumentattributes.md) Methode.

## <a name="requirements"></a>Anforderungen
 Header: msdbg.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Siehe auch
- [Enumerationen](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [onUpdateDocumentAttributes](../../../extensibility/debugger/reference/idebugdocumenttextevents2-onupdatedocumentattributes.md)