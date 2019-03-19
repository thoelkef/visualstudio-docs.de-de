---
title: IMachineDebugManager-Schnittstelle | Microsoft-Dokumentation
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
ms.openlocfilehash: 6db8989fc6c932723a9b95017854635396b0deda
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/19/2019
ms.locfileid: "58157960"
---
# <a name="imachinedebugmanager-interface"></a>IMachineDebugManager-Schnittstelle
Die primäre Schnittstelle für die Debug-Manager werden soll. Diese Schnittstelle ähnelt der `IMachineDebugManagerCookie` Schnittstelle.  
  
 Zusätzlich zu den von geerbten Methoden `IUnknown`, `IMachineDebugManager` Schnittstelle verfügbar macht, die folgenden Methoden.  
  
## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge  
  
|Methode|Beschreibung|  
|------------|-----------------|  
|[IMachineDebugManager::AddApplication](../../winscript/reference/imachinedebugmanager-addapplication.md)|Fügt eine Anwendung in der ausgeführten Anwendungsliste.|  
|[IMachineDebugManager::RemoveApplication](../../winscript/reference/imachinedebugmanager-removeapplication.md)|Entfernt eine Anwendung aus der ausgeführten Anwendungsliste.|  
|[IMachineDebugManager::EnumApplications](../../winscript/reference/imachinedebugmanager-enumapplications.md)|Gibt einen Enumerator, der die aktuelle Liste ausgeführter Anwendungen.|  
  
## <a name="see-also"></a>Siehe auch  
 [IMachineDebugManagerCookie-Schnittstelle](../../winscript/reference/imachinedebugmanagercookie-interface.md)