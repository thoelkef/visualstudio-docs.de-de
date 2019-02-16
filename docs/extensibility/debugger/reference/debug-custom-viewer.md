---
title: DEBUG_CUSTOM_VIEWER | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- DEBUG_CUSTOM_VIEWER
helpviewer_keywords:
- DEBUG_CUSTOM_VIEWER structure
ms.assetid: 8e0ef3f0-0107-48e8-a037-6e52b4c4ed9d
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: fe17c8747d5c678c14561a918ddd9d62bd658841
ms.sourcegitcommit: 752f03977f45169585e407ef719450dbe219b7fc
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/15/2019
ms.locfileid: "56315832"
---
# <a name="debugcustomviewer"></a>DEBUG_CUSTOM_VIEWER
Eine Struktur, die einen benutzerdefinierten Viewer identifiziert, oder geben Sie die Schnellansicht.

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
dwID  
Eine ID, mehrere Viewer oder Schnellansichten, die von einer Implementierung zu unterscheiden `GUID`.

bstrMenuName  
Der Text, der im Dropdown-Menü angezeigt wird.

bstrDescription  
Eine Beschreibung der benutzerdefinierten Viewer oder typschnellansicht (muss ein null-Wert sein, wenn nicht verwendet).

guidLang  
Sprache für die ausdrucksauswertung bereitstellt.

guidVendor  
Hersteller, der die ausdrucksauswertung bereitstellt.

bstrMetric  
Metrik unter dem die benutzerdefinierten Viewer oder typschnellansicht `CLSID` wird gespeichert.

## <a name="remarks"></a>Hinweise
Eine Liste dieser Struktur wird zurückgegeben, durch einen Aufruf der [GetCustomViewerList](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md) Methode (und durch Erweiterung, die [GetCustomViewerList](../../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewerlist.md) Methode).

## <a name="requirements"></a>Anforderungen
Header: msdbg.h

Namespace: Microsoft.VisualStudio.Debugger.Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Siehe auch
[Strukturen und Unions](../../../extensibility/debugger/reference/structures-and-unions.md)  
[GetCustomViewerList](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md)  
[GetCustomViewerList](../../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewerlist.md)
