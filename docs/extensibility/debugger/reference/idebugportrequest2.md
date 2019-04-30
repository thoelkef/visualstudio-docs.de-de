---
title: IDebugPortRequest2 | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPortRequest2
helpviewer_keywords:
- IDebugPortRequest2 interface
ms.assetid: 556e610d-7c4b-44a8-965a-76a9d02b601a
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8e2b78986b997358d7f15c9c8c73bb4bd0f73aaf
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62871479"
---
# <a name="idebugportrequest2"></a>IDebugPortRequest2
Diese Schnittstelle wird beschrieben, einen Port. Diese Beschreibung wird verwendet, um den Port an einen Lieferanten Port hinzuzufügen.

## <a name="syntax"></a>Syntax

```
IDebugPortRequest2 : IUnknown
```

## <a name="notes-for-implementers"></a>Hinweise für Implementierer
 Diese Schnittstelle beim Abrufen eines Debug-Ports von eines portanbieters wird von Visual Studio in der Regel implementiert.

## <a name="notes-for-callers"></a>Hinweise für Aufrufer
 Diese Schnittstelle übergebenen [Port hinzufügen](../../../extensibility/debugger/reference/idebugportsupplier2-addport.md) So erstellen Sie einen Debugport. Ein Aufruf von [GetPortRequest](../../../extensibility/debugger/reference/idebugport2-getportrequest.md) gibt diese Schnittstelle, die die Anforderung verwendet, um die im ersten Schritt erstellen Sie den Port darstellt.

## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge
 Die folgende Tabelle zeigt die Methoden der `IDebugPortRequest2`.

|Methode|Beschreibung|
|------------|-----------------|
|[GetPortName](../../../extensibility/debugger/reference/idebugportrequest2-getportname.md)|Ruft den Namen des Ports erstellen.|

## <a name="remarks"></a>Hinweise
 Eine Debug-Engine ist in der Regel interagiert nicht mit eines portanbieters und hat keine Verwendung für diese Schnittstelle.

## <a name="requirements"></a>Anforderungen
 Header: msdbg.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Siehe auch
- [Wichtige Schnittstellen](../../../extensibility/debugger/reference/core-interfaces.md)
- [AddPort](../../../extensibility/debugger/reference/idebugportsupplier2-addport.md)
- [GetPortRequest](../../../extensibility/debugger/reference/idebugport2-getportrequest.md)