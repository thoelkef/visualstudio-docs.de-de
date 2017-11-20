---
title: IMachineDebugManagerCookie-Schnittstelle | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords: IMachineDebugManagerCookie interface
ms.assetid: 04770935-3ccf-41e9-b0c1-c78376ab1e3c
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a03b959a7eb09f3b85530bbba07d1d2dc7f8948a
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="imachinedebugmanagercookie-interface"></a>IMachineDebugManagerCookie-Schnittstelle
Ähnlich wie die `IMachineDebugManager` -Schnittstelle, die `IMachineDebugManagerCookie` Schnittstelle Debug Cookies unterstützt.  
  
 Diese Schnittstelle (zusammen mit der `IDebugCookie` Schnittstelle) ermöglichen, dass in einem Skript-Debugger-Prozess ausgeführt wird, ohne dass der Debugger nachverfolgen diese Skripts von Skripts.  
  
 Ein Script-Debugger Ruft die `IDebugCookie::SetDebugCookie` Methode auf den Prozess Debuggen-Manager (PDM). Klicken Sie dann die PDM sendet dieses Cookie wird zusammen mit jeder Anforderung zum Hinzufügen oder entfernen eine skriptanwendung oder über die Computer Debuggen Manager (MDM), mit den Methoden der der `IMachineDebugManagerCookie` Schnittstelle. Die MDM benachrichtigt dann jede Debugger der Änderung, mit Ausnahme von derjenige, der das Cookie wurde.  
  
 Zusätzlich zu den von geerbten Methoden `IUnknown`, `IMachineDebugManagerCookie` Schnittstelle macht die folgenden Methoden verfügbar.  
  
## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge  
  
|Methode|Beschreibung|  
|------------|-----------------|  
|[IMachineDebugManagerCookie::AddApplication](../../winscript/reference/imachinedebugmanagercookie-addapplication.md)|Fügt eine Anwendung mit der Ausführung Anwendungsliste.|  
|[IMachineDebugManagerCookie::EnumApplications](../../winscript/reference/imachinedebugmanagercookie-enumapplications.md)|Gibt einen Enumerator, der die aktuelle Liste von ausgeführten Anwendungen.|  
|[IMachineDebugManagerCookie::RemoveApplication](../../winscript/reference/imachinedebugmanagercookie-removeapplication.md)|Entfernt eine Anwendung aus der Ausführung Anwendungsliste.|  
  
## <a name="see-also"></a>Siehe auch  
 [IMachineDebugManager-Schnittstelle](../../winscript/reference/imachinedebugmanager-interface.md)   
 [IDebugCookie-Schnittstelle](../../winscript/reference/idebugcookie-interface.md)