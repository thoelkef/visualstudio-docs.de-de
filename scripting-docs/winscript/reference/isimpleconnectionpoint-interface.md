---
title: ISimpleConnectionPoint-Schnittstelle | Microsoft-Dokumentation
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
ms.openlocfilehash: 0d18c8f9eef6ddb1a38473eb19984bd9cf7dbd96
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/19/2019
ms.locfileid: "58146928"
---
# <a name="isimpleconnectionpoint-interface"></a>ISimpleConnectionPoint-Schnittstelle
Bietet eine einfache Möglichkeit zum Beschreiben und Aufzählen der Ereignisse, die ausgelöst wird, an einem bestimmten Verbindungspunkt. Diese Schnittstelle erleichtert auch zum Einbinden einer `IDispatch` Objekt für diese Ereignisse. Diese Schnittstelle wird durch den Prozess Debug-Manager (PDM) implementiert und von der Skript-Engines genutzt werden.  
  
 Diese Schnittstelle steht `IDebugHelper::CreateSimpleConnectionPoint`.  
  
 Zusätzlich zu den von geerbten Methoden `IUnknown`, `ISimpleConnectionPoint` Schnittstelle verfügbar macht, die folgenden Methoden.  
  
## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge  
  
|Methode|Beschreibung|  
|------------|-----------------|  
|[ISimpleConnectionPoint::Advise](../../winscript/reference/isimpleconnectionpoint-advise.md)|Herstellen einer Verbindung zwischen der einfachen Verbindungspunktobjekt und die Senke des Clients.|  
|[ISimpleConnectionPoint::DescribeEvents](../../winscript/reference/isimpleconnectionpoint-describeevents.md)|Gibt den DISPID und den Namen für jedes Ereignis in einem angegebenen Bereich von Ereignissen zurück.|  
|[ISimpleConnectionPoint::GetEventCount](../../winscript/reference/isimpleconnectionpoint-geteventcount.md)|Gibt die Anzahl von Ereignissen, die für diese Schnittstelle verfügbar gemacht werden.|  
|[ISimpleConnectionPoint::Unadvise](../../winscript/reference/isimpleconnectionpoint-unadvise.md)|Beendet eine Advise-Verbindung, die zuvor über `ISimpleConnectionPoint::Advise`.|  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugProperty-Schnittstelle](../../winscript/reference/idebugproperty-interface.md)