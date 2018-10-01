---
title: IDebugPortPicker | Microsoft-Dokumentation
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- IDebugPortPicker interface
ms.assetid: 8b7f6685-a3c5-4355-b706-c1b574f6ff84
caps.latest.revision: 9
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 1b92f188dd2bed678e4117adde7c61d8844e8360
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47520868"
---
# <a name="idebugportpicker"></a>IDebugPortPicker
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [IDebugPortPicker](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugportpicker).  
  
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

