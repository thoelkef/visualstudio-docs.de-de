---
title: Isimpleconnectionpoint-Schnittstelle | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- ISimpleConnectionPoint interface
ms.assetid: f632a82f-942d-4291-963e-e9fa2b162493
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 549d7f38b01937f992b240cb6f1d651bc848236c
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/18/2019
ms.locfileid: "72571791"
---
# <a name="isimpleconnectionpoint-interface"></a>ISimpleConnectionPoint-Schnittstelle
Bietet eine einfache Möglichkeit zum beschreiben und Aufzählen der Ereignisse, die an einem bestimmten Verbindungspunkt ausgelöst werden. Diese Schnittstelle vereinfacht auch das anstecken eines `IDispatch` Objekts für diese Ereignisse. Diese Schnittstelle wird vom Process Debug Manager (PDM) implementiert und von Skript Modulen verwendet.  
  
 Diese Schnittstelle ist über `IDebugHelper::CreateSimpleConnectionPoint` verfügbar.  
  
 Zusätzlich zu den Methoden, die von `IUnknown` geerbt werden, macht die `ISimpleConnectionPoint`-Schnittstelle die folgenden Methoden verfügbar.  
  
## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge  
  
|Methode|Beschreibung|  
|------------|-----------------|  
|[ISimpleConnectionPoint::Advise](../../winscript/reference/isimpleconnectionpoint-advise.md)|Stellt eine Verbindung zwischen dem einfachen Verbindungspunkt Objekt und der Senke des Clients her.|  
|[ISimpleConnectionPoint::DescribeEvents](../../winscript/reference/isimpleconnectionpoint-describeevents.md)|Gibt die DISPID und den Namen für jedes Ereignis in einem angegebenen Bereich von Ereignissen zurück.|  
|[ISimpleConnectionPoint::GetEventCount](../../winscript/reference/isimpleconnectionpoint-geteventcount.md)|Gibt die Anzahl der für diese Schnittstelle verfügbar gemachten Ereignisse zurück.|  
|[ISimpleConnectionPoint::Unadvise](../../winscript/reference/isimpleconnectionpoint-unadvise.md)|Beendet eine Beratungs Verbindung, die zuvor über `ISimpleConnectionPoint::Advise` hergestellt wurde.|  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugProperty-Schnittstelle](../../winscript/reference/idebugproperty-interface.md)