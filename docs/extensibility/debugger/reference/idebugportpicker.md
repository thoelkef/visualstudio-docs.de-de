---
title: IDebugPortPicker | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- IDebugPortPicker interface
ms.assetid: 8b7f6685-a3c5-4355-b706-c1b574f6ff84
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 753303ecc5a3b3f66fe8135a5955308c0cf4e586
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/25/2019
ms.locfileid: "54957594"
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