---
title: IDebugApplicationNodeEvents-Schnittstelle | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDebugApplicationNodeEvents interface
ms.assetid: 02e0bb17-84ce-458b-bae6-608a9899e535
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7412e258c7f67f44bde6f69b593a1eecb1d84e07
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/19/2019
ms.locfileid: "58150511"
---
# <a name="idebugapplicationnodeevents-interface"></a>IDebugApplicationNodeEvents-Schnittstelle
Stellt die Ereignisschnittstelle für die `IDebugApplicationNode`-Schnittstelle bereit.  
  
 Zusätzlich zu den von geerbten Methoden `IUnknown`, `IDebugApplicationNodeEvents` Schnittstelle verfügbar macht, die folgenden Methoden.  
  
## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge  
  
|Methode|Beschreibung|  
|------------|-----------------|  
|[IDebugApplicationNodeEvents::onAddChild](../../winscript/reference/idebugapplicationnodeevents-onaddchild.md)|Behandelt das Ereignis, wenn ein Debug-Anwendungsobjekt Knoten ein untergeordneter Knoten hinzugefügt wird.|  
|[IDebugApplicationNodeEvents::onRemoveChild](../../winscript/reference/idebugapplicationnodeevents-onremovechild.md)|Behandelt das Ereignis, wenn ein untergeordneter Knoten aus einer Debug-Anwendungsobjekt Knoten entfernt wird.|  
|[IDebugApplicationNodeEvents::onDetach](../../winscript/reference/idebugapplicationnodeevents-ondetach.md)|Behandelt ein Ereignis gibt an, dass das Debug-Anwendungsobjekt Knoten von einem übergeordneten Knoten getrennt wurde.|  
|[IDebugApplicationNodeEvents::onAttach](../../winscript/reference/idebugapplicationnodeevents-onattach.md)|Behandelt ein Ereignis gibt an, dass das Debug-Anwendungsobjekt Knoten an einem übergeordneten Knoten angefügt wurde.|  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugApplicationNode-Schnittstelle](../../winscript/reference/idebugapplicationnode-interface.md)