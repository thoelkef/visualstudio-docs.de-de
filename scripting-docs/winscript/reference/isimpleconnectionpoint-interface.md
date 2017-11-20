---
title: ISimpleConnectionPoint-Schnittstelle | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords: ISimpleConnectionPoint interface
ms.assetid: f632a82f-942d-4291-963e-e9fa2b162493
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: de40f66a9e5721b8dacac634c6fb77982017c155
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="isimpleconnectionpoint-interface"></a>ISimpleConnectionPoint-Schnittstelle
Bietet eine einfache Möglichkeit zum Beschreiben und beim Aufzählen der Ereignisse, die ausgelöst wird, auf einem bestimmten Verbindungspunkt. Diese Schnittstelle vereinfacht außerdem die Einbindung ein `IDispatch` Objekt für diese Ereignisse. Diese Schnittstelle wird durch den Prozess Debuggen-Manager (PDM) implementiert und von Script-Module genutzt.  
  
 Diese Schnittstelle ist verfügbar von `IDebugHelper::CreateSimpleConnectionPoint`.  
  
 Zusätzlich zu den von geerbten Methoden `IUnknown`, `ISimpleConnectionPoint` Schnittstelle macht die folgenden Methoden verfügbar.  
  
## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge  
  
|Methode|Beschreibung|  
|------------|-----------------|  
|[ISimpleConnectionPoint::Advise](../../winscript/reference/isimpleconnectionpoint-advise.md)|Herstellen einer Verbindung zwischen der einfachen Verbindungspunktobjekt und der Client-Senke.|  
|[ISimpleConnectionPoint::DescribeEvents](../../winscript/reference/isimpleconnectionpoint-describeevents.md)|Gibt den DISPID und den Namen für jedes Ereignis in einem angegebenen Bereich von Ereignissen zurück.|  
|[ISimpleConnectionPoint::GetEventCount](../../winscript/reference/isimpleconnectionpoint-geteventcount.md)|Gibt die Anzahl der Ereignisse, die für diese Schnittstelle verfügbar gemacht werden.|  
|[ISimpleConnectionPoint::Unadvise](../../winscript/reference/isimpleconnectionpoint-unadvise.md)|Beendet eine Advise-Verbindung, die zuvor über `ISimpleConnectionPoint::Advise`.|  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugProperty-Schnittstelle](../../winscript/reference/idebugproperty-interface.md)