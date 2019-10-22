---
title: Imachinedebugmanagercookie-Schnittstelle | Microsoft-Dokumentation
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
ms.openlocfilehash: 6b39c286f389c99187b0f3250fc68af92ff5dcc8
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/18/2019
ms.locfileid: "72573887"
---
# <a name="imachinedebugmanagercookie-interface"></a>IMachineDebugManagerCookie-Schnittstelle
Ähnlich wie bei der `IMachineDebugManager`-Schnittstelle unterstützt die `IMachineDebugManagerCookie`-Schnittstelle Debug-Cookies.  
  
 Mit dieser Schnittstelle (zusammen mit der `IDebugCookie`-Schnittstelle) können Skripts in einem Skript Debugger-Prozess ausgeführt werden, ohne dass der Debugger diese Skripts nachverfolgen muss.  
  
 Ein Skript Debugger ruft die `IDebugCookie::SetDebugCookie`-Methode für den Process Debug Manager (PDM) auf. Anschließend sendet das PDM dieses Cookie zusammen mit allen Anforderungen zum Hinzufügen oder Entfernen einer Skript Anwendung zum bzw. aus dem Machine Debug Manager (MDM) mithilfe der Methoden der `IMachineDebugManagerCookie`-Schnittstelle. Die MDM benachrichtigt dann jeden Debugger über die Änderung, mit Ausnahme derjenigen, die über dieses Cookie verfügt.  
  
 Zusätzlich zu den Methoden, die von `IUnknown` geerbt werden, macht die `IMachineDebugManagerCookie`-Schnittstelle die folgenden Methoden verfügbar.  
  
## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge  
  
|Methode|Beschreibung|  
|------------|-----------------|  
|[IMachineDebugManagerCookie::AddApplication](../../winscript/reference/imachinedebugmanagercookie-addapplication.md)|Fügt der Liste der laufenden Anwendungen eine Anwendung hinzu.|  
|[IMachineDebugManagerCookie::EnumApplications](../../winscript/reference/imachinedebugmanagercookie-enumapplications.md)|Gibt einen Enumerator der aktuellen Liste ausgelaufteter Anwendungen zurück.|  
|[IMachineDebugManagerCookie::RemoveApplication](../../winscript/reference/imachinedebugmanagercookie-removeapplication.md)|Entfernt eine Anwendung aus der Liste der laufenden Anwendungen.|  
  
## <a name="see-also"></a>Siehe auch  
 [Imachinedebugmanager-Schnittstelle](../../winscript/reference/imachinedebugmanager-interface.md)    
 [IDebugCookie-Schnittstelle](../../winscript/reference/idebugcookie-interface.md)