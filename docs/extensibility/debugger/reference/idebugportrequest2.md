---
title: IDebugPortRequest2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPortRequest2
helpviewer_keywords:
- IDebugPortRequest2 interface
ms.assetid: 556e610d-7c4b-44a8-965a-76a9d02b601a
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 163718fda344ba5f3f44ef630b4eba3e5613dc61
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80724787"
---
# <a name="idebugportrequest2"></a>IDebugPortRequest2
Diese Schnittstelle beschreibt einen Port. Diese Beschreibung wird verwendet, um den Port zu einem Portlieferanten hinzuzufügen.

## <a name="syntax"></a>Syntax

```
IDebugPortRequest2 : IUnknown
```

## <a name="notes-for-implementers"></a>Hinweise für Implementierer
 Visual Studio implementiert diese Schnittstelle in der Regel beim Abrufen eines Debugports von einem Portanbieter.

## <a name="notes-for-callers"></a>Hinweise für Anrufer
 Diese Schnittstelle wird an [AddPort](../../../extensibility/debugger/reference/idebugportsupplier2-addport.md) übergeben, um einen Debugport zu erstellen. Ein Aufruf von [GetPortRequest](../../../extensibility/debugger/reference/idebugport2-getportrequest.md) gibt diese Schnittstelle zurück, die die Anforderung darstellt, die verwendet wird, um den Port überhaupt zu erstellen.

## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge
 Die folgende Tabelle zeigt `IDebugPortRequest2`die Methoden von .

|Methode|BESCHREIBUNG|
|------------|-----------------|
|[GetPortName](../../../extensibility/debugger/reference/idebugportrequest2-getportname.md)|Ruft den Namen des zu erstellenden Ports ab.|

## <a name="remarks"></a>Bemerkungen
 Ein Debugmodul interagiert in der Regel nicht mit einem Portlieferanten und hat keine Verwendung für diese Schnittstelle.

## <a name="requirements"></a>Requirements (Anforderungen)
 Kopfzeile: msdbg.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Weitere Informationen
- [Wichtige Schnittstellen](../../../extensibility/debugger/reference/core-interfaces.md)
- [AddPort](../../../extensibility/debugger/reference/idebugportsupplier2-addport.md)
- [GetPortRequest](../../../extensibility/debugger/reference/idebugport2-getportrequest.md)
