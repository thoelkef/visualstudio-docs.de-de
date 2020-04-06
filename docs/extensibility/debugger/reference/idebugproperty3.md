---
title: IDebugProperty3 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProperty3
helpviewer_keywords:
- IDebugProperty3 interface
ms.assetid: 8f9be68d-4490-4eca-8f6b-8a10ed77e226
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d2819724c204631112fd1a3e827126c4bc176972
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80721042"
---
# <a name="idebugproperty3"></a>IDebugProperty3
Diese Schnittstelle bietet Unterstützung für:

- Abrufen einer beliebig langen Zeichenfolge, die der Eigenschaft zugeordnet ist.

- Zuordnen einer eindeutigen ID zur Eigenschaft.

- Abrufen einer Liste benutzerdefinierter Viewer für die Eigenschaft.

- Festlegen des Werts einer Eigenschaft mit der Möglichkeit, resultierende Fehler zu melden

## <a name="syntax"></a>Syntax

```
IDebugProperty3 : IDebugProperty2
```

## <a name="notes-for-implementers"></a>Hinweise für Implementierer
 Das Debugmodul (DE) implementiert diese Schnittstelle für dasselbe Objekt, das [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) implementiert, um Unterstützung für lange Zeichenfolgen, Eigenschafts-IDs und benutzerdefinierte Viewer bereitzustellen.

## <a name="notes-for-callers"></a>Hinweise für Anrufer
 Rufen Sie [QueryInterface](/cpp/atl/queryinterface) auf einer `IDebugProperty2` Schnittstelle auf, um diese Schnittstelle zu erhalten.

## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge
 Zusätzlich zu den Methoden, `IDebugProperty2`die `IDebugProperty3` von geerbt wurden, macht die Schnittstelle die folgenden Methoden verfügbar.

|Methode|BESCHREIBUNG|
|------------|-----------------|
|[GetStringCharLength](../../../extensibility/debugger/reference/idebugproperty3-getstringcharlength.md)|Gibt die Länge der Zeichenfolge zurück, die der Eigenschaft zugeordnet ist.|
|[GetStringChars](../../../extensibility/debugger/reference/idebugproperty3-getstringchars.md)|Gibt die Zeichenfolge in einem vom Benutzer bereitgestellten Puffer zurück.|
|[CreateObjectID](../../../extensibility/debugger/reference/idebugproperty3-createobjectid.md)|Erstellt eine eindeutige ID für diese Eigenschaft.|
|[DestroyObjectID](../../../extensibility/debugger/reference/idebugproperty3-destroyobjectid.md)|Zerstört die eindeutige ID für diese Eigenschaft.|
|[GetCustomViewerCount](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewercount.md)|Gibt die Anzahl der benutzerdefinierten Viewer zurück, mit denen diese Eigenschaft angezeigt werden kann.|
|[GetCustomViewerList](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md)|Gibt die Liste der benutzerdefinierten Viewer zurück, mit denen diese Eigenschaft angezeigt werden kann.|
|[SetValueAsStringWithError](../../../extensibility/debugger/reference/idebugproperty3-setvalueasstringwitherror.md)|Legt den Wert dieser Eigenschaft fest und gibt eine Fehlermeldung zurück, wenn etwas schief gelaufen ist.|

## <a name="remarks"></a>Bemerkungen
- [SetValueAsStringWithError](../../../extensibility/debugger/reference/idebugproperty3-setvalueasstringwitherror.md) ist die bevorzugte Methode für den Sitzungsdebug-Manager (SDM), den Wert einer Eigenschaft festzulegen.

## <a name="requirements"></a>Requirements (Anforderungen)
 Kopfzeile: msdbg.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Weitere Informationen
- [Wichtige Schnittstellen](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
- [IDebugCustomViewer](../../../extensibility/debugger/reference/idebugcustomviewer.md)
