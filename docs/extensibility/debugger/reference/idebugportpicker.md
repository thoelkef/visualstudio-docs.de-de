---
title: IDebugPortPicker | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugPortPicker interface
ms.assetid: 8b7f6685-a3c5-4355-b706-c1b574f6ff84
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 845e197b186d462b74aaf8cf3cd7218e4606dfc7
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/22/2019
ms.locfileid: "56716544"
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