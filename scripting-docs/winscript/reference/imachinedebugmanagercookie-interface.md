---
title: IMachineDebugManagerCookie-Schnittstelle | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IMachineDebugManagerCookie interface
ms.assetid: 04770935-3ccf-41e9-b0c1-c78376ab1e3c
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: fdc02498360f2e3900012166474c5d1e35abd6ee
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/19/2019
ms.locfileid: "58151049"
---
# <a name="imachinedebugmanagercookie-interface"></a>IMachineDebugManagerCookie-Schnittstelle
Ähnlich wie die `IMachineDebugManager` -Schnittstelle, die `IMachineDebugManagerCookie` Schnittstelle unterstützt die Debug-Cookies.  
  
 Diese Schnittstelle (zusammen mit den `IDebugCookie` Schnittstelle)-Skripts in einem Skript-Debugger-Prozess ausgeführt wird, ohne dass der Debugger diese Skripts mitverfolgen können.  
  
 Ruft ein Script-Debugger den `IDebugCookie::SetDebugCookie` Methode für den Prozess Debug-Manager (PDM). Klicken Sie dann das PDM sendet dieses Cookie wird zusammen mit jeder Anforderung zum Hinzufügen oder entfernen eine skriptanwendung in oder aus der Computer Debug-Manager (MDM) mit den Methoden der der `IMachineDebugManagerCookie` Schnittstelle. Anschließend benachrichtigt der MDM alle Debugger der Änderung an, mit Ausnahme der, die das Cookie.  
  
 Zusätzlich zu den von geerbten Methoden `IUnknown`, `IMachineDebugManagerCookie` Schnittstelle verfügbar macht, die folgenden Methoden.  
  
## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge  
  
|Methode|Beschreibung|  
|------------|-----------------|  
|[IMachineDebugManagerCookie::AddApplication](../../winscript/reference/imachinedebugmanagercookie-addapplication.md)|Fügt eine Anwendung in der ausgeführten Anwendungsliste.|  
|[IMachineDebugManagerCookie::EnumApplications](../../winscript/reference/imachinedebugmanagercookie-enumapplications.md)|Gibt einen Enumerator, der die aktuelle Liste ausgeführter Anwendungen.|  
|[IMachineDebugManagerCookie::RemoveApplication](../../winscript/reference/imachinedebugmanagercookie-removeapplication.md)|Entfernt eine Anwendung aus der ausgeführten Anwendungsliste.|  
  
## <a name="see-also"></a>Siehe auch  
 [IMachineDebugManager-Schnittstelle](../../winscript/reference/imachinedebugmanager-interface.md)   
 [IDebugCookie-Schnittstelle](../../winscript/reference/idebugcookie-interface.md)