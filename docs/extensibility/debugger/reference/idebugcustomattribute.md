---
title: IDebugCustomAttribute | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCustomAttribute
helpviewer_keywords:
- IDebugCustomAttribute interface
ms.assetid: c5ae41e9-00b9-4cca-871d-b8de9ef390d1
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a31133139d0104cd29f5d0d0e760bd78ec5783fd
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80732678"
---
# <a name="idebugcustomattribute"></a>IDebugCustomAttribute
Diese Schnittstelle stellt ein benutzerdefiniertes Attribut dar und kann den Namen, den übergeordneten und den Klassentyp des Attributs bereitstellen.

## <a name="syntax"></a>Syntax

```
IDebugCustomAttribute : IUnknown
```

## <a name="notes-for-implementers"></a>Hinweise für Implementierer
 Ein Symbolanbieter implementiert diese Schnittstelle, um benutzerdefinierte Attribute zu unterstützen, die einem Symbol zugeordnet sind. Es wird in der Regel für sein eigenes Objekt implementiert.

## <a name="notes-for-callers"></a>Hinweise für Anrufer
 Ein Aufruf von [Next](../../../extensibility/debugger/reference/ienumdebugcustomattributes-next.md) gibt diese Schnittstelle zurück. Ein Aufruf der [EnumCustomAttributes-Methode](../../../extensibility/debugger/reference/idebugcustomattributequery2-enumcustomattributes.md) gibt die [IEnumDebugCustomAttributes-Schnittstelle](../../../extensibility/debugger/reference/ienumdebugcustomattributes.md) zurück.

## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge
 Die folgende Tabelle zeigt `IDebugCustomAttribute`die Methoden von .

|Methode|BESCHREIBUNG|
|------------|-----------------|
|[GetParentField](../../../extensibility/debugger/reference/idebugcustomattribute-getparentfield.md)|Ruft das Feld ab, dem das aktuelle Attribut zugeordnet ist.|
|[GetAttributeTypeField](../../../extensibility/debugger/reference/idebugcustomattribute-getattributetypefield.md)|Ruft den benutzerdefinierten Attributklassentyp ab.|
|[GetName](../../../extensibility/debugger/reference/idebugcustomattribute-getname.md)|Ruft den Namen des benutzerdefinierten Attributs ab.|
|[GetAttributeBytes](../../../extensibility/debugger/reference/idebugcustomattribute-getattributebytes.md)|Ruft die Attributinformationen als Bytes-Blob ab.|

## <a name="remarks"></a>Bemerkungen
 Ein benutzerdefiniertes Attribut ist eine Struktur für C, die benutzerdefinierte Metadaten bereitstellt, die einer bestimmten Klasse oder Methode zugeordnet sind.

## <a name="requirements"></a>Requirements (Anforderungen)
 Kopfzeile: sh.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Weitere Informationen
- [Symbol Provider Interfaces](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
- [IDebugCustomAttributeQuery2](../../../extensibility/debugger/reference/idebugcustomattributequery2.md)
- [IEnumDebugCustomAttributes](../../../extensibility/debugger/reference/ienumdebugcustomattributes.md)
