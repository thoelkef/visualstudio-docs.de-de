---
title: DEBUG_CUSTOM_VIEWER | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DEBUG_CUSTOM_VIEWER
helpviewer_keywords:
- DEBUG_CUSTOM_VIEWER structure
ms.assetid: 8e0ef3f0-0107-48e8-a037-6e52b4c4ed9d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 3de9b8f7ef30cffbdd78399dc831060e413ba51b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80737544"
---
# <a name="debug_custom_viewer"></a>DEBUG_CUSTOM_VIEWER
Eine Struktur, die einen benutzerdefinierten Viewer oder eine Typvisualisierung identifiziert.

## <a name="syntax"></a>Syntax

```cpp
typedef struct tagDEBUG_CUSTOM_VIEWER {
    DWORD dwID;
    BSTR  bstrMenuName;
    BSTR  bstrDescription;
    GUID  guidLang;
    GUID  guidVendor;
    BSTR  bstrMetric;
} DEBUG_CUSTOM_VIEWER;
```

```csharp
public struct DEBUG_CUSTOM_VIEWER {
    public uint   dwID;
    public string bstrMenuName;
    public string bstrDescription;
    public Guid   guidLang;
    public Guid   guidVendor;
    public string bstrMetric;
};
```

## <a name="members"></a>Member
`dwID`\
Eine ID zum Unterscheiden mehrerer Viewer oder `GUID`Visualisierer, die von einem implementiert werden.

`bstrMenuName`\
Der Text, der im Dropdown-Menü angezeigt wird.

`bstrDescription`\
Eine Beschreibung des benutzerdefinierten Viewers oder Typvisualizers (muss ein NULL-Wert sein, wenn er nicht verwendet wird).

`guidLang`\
Sprache des liefernden Ausdrucksevaluators.

`guidVendor`\
Anbieter des bereitstellenden Ausdrucksevaluators.

`bstrMetric`\
Metrik, unter der der `CLSID` benutzerdefinierte Viewer oder die Typvisualisierung gespeichert wird.

## <a name="remarks"></a>Bemerkungen
Eine Liste dieser Struktur wird durch einen Aufruf der [GetCustomViewerList-Methode](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md) (und damit der [GetCustomViewerList-Methode)](../../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewerlist.md) zurückgegeben.

## <a name="requirements"></a>Requirements (Anforderungen)
Kopfzeile: msdbg.h

Namespace: Microsoft.VisualStudio.Debugger.Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Weitere Informationen
- [Structures and Unions](../../../extensibility/debugger/reference/structures-and-unions.md)
- [GetCustomViewerList](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md)
- [GetCustomViewerList](../../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewerlist.md)
