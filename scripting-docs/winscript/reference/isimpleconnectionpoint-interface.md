---
title: ISimpleConnectionPoint-Schnittstelle | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: 4a756fa3f933f4adff56c41a86aee19a0a2a93aa
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/16/2019
ms.locfileid: "54346409"
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