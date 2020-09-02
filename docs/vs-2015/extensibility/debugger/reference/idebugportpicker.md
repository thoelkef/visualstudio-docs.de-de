---
title: Idebugportpicker | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- IDebugPortPicker interface
ms.assetid: 8b7f6685-a3c5-4355-b706-c1b574f6ff84
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: f3e030facd8c70aec4fdc480b01c90ee4c0acda7
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68188388"
---
# <a name="idebugportpicker"></a>IDebugPortPicker
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Stellt eine angepasste Benutzeroberfläche zum Auswählen des Ports dar.  
  
## <a name="syntax"></a>Syntax  
  
```  
IDebugPortPicker : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Hinweise für Implementierer  
 Diese Schnittstelle wird von Port Lieferanten implementiert. Ein Port Lieferant definiert seine Port Auswahl, indem er ihn als CLSID verfügbar macht und die `metricPortPickerCLSID` Metrik an der verfügbar gemachten CLSID zeigt.  
  
## <a name="methods"></a>Methoden  
 In der folgenden Tabelle sind die Methoden von aufgeführt `IDebugPortPicker` .  
  
|Methode|Beschreibung|  
|------------|-----------------|  
|[DisplayPortPicker](../../../extensibility/debugger/reference/idebugportpicker-displayportpicker.md)|Zeigt das angegebene Dialogfeld an, in dem der Benutzer einen Port auswählen kann.|  
|[SetSite](../../../extensibility/debugger/reference/idebugportpicker-setsite.md)|Legt den Dienstanbieter fest.|  
  
## <a name="requirements"></a>Anforderungen  
 Header: msdbg. h  
  
 Namespace: Microsoft. VisualStudio. Debugger. Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll
