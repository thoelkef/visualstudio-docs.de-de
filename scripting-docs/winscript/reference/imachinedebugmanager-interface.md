---
title: Imachinedebugmanager-Schnittstelle | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IMachineDebugManager interface
ms.assetid: 0b7133bb-5a52-4036-b4db-d69260790db7
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9d491b03ba04d346e3a14a08d5e2b6b9d34c7d97
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/18/2019
ms.locfileid: "72573920"
---
# <a name="imachinedebugmanager-interface"></a>IMachineDebugManager-Schnittstelle
Die primäre Schnittstelle zum Machine Debug-Manager. Diese Schnittstelle ähnelt der `IMachineDebugManagerCookie`-Schnittstelle.  
  
 Zusätzlich zu den Methoden, die von `IUnknown` geerbt werden, macht die `IMachineDebugManager`-Schnittstelle die folgenden Methoden verfügbar.  
  
## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge  
  
|Methode|Beschreibung|  
|------------|-----------------|  
|[IMachineDebugManager::AddApplication](../../winscript/reference/imachinedebugmanager-addapplication.md)|Fügt der Liste der laufenden Anwendungen eine Anwendung hinzu.|  
|[IMachineDebugManager::RemoveApplication](../../winscript/reference/imachinedebugmanager-removeapplication.md)|Entfernt eine Anwendung aus der Liste der laufenden Anwendungen.|  
|[IMachineDebugManager::EnumApplications](../../winscript/reference/imachinedebugmanager-enumapplications.md)|Gibt einen Enumerator der aktuellen Liste ausgelaufteter Anwendungen zurück.|  
  
## <a name="see-also"></a>Siehe auch  
 [IMachineDebugManagerCookie-Schnittstelle](../../winscript/reference/imachinedebugmanagercookie-interface.md)