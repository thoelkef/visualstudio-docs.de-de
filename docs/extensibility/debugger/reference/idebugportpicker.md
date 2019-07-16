---
title: IDebugPortPicker | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugPortPicker interface
ms.assetid: 8b7f6685-a3c5-4355-b706-c1b574f6ff84
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 991480886c2c43c330ce37561d383ffdc420e214
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/29/2019
ms.locfileid: "66340365"
---
# <a name="idebugportpicker"></a>IDebugPortPicker
Stellt eine benutzerdefinierte Benutzeroberfläche für die Auswahl des Ports dar.

## <a name="syntax"></a>Syntax

```
IDebugPortPicker : IUnknown
```

## <a name="notes-for-implementers"></a>Hinweise für Implementierer
 Diese Schnittstelle wird von Portanbieter implementiert. Ein portanbieters definiert ihre Auswahl Port, indem Sie es als eine CLSID verfügbar zu machen, und zeigen die `metricPortPickerCLSID` Metrik an die verfügbar gemachten CLSID.

## <a name="methods"></a>Methoden
 Die folgende Tabelle zeigt die Methoden der `IDebugPortPicker`.

|Methode|Beschreibung|
|------------|-----------------|
|[DisplayPortPicker](../../../extensibility/debugger/reference/idebugportpicker-displayportpicker.md)|Zeigt das angegebene Dialogfeld an, das dem Benutzer ermöglicht, einen Port auszuwählen.|
|[SetSite](../../../extensibility/debugger/reference/idebugportpicker-setsite.md)|Legt den Dienstanbieter fest.|

## <a name="requirements"></a>Anforderungen
 Header: Msdbg.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll