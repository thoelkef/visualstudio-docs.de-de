---
title: IDebugApplicationNodeEvents-Schnittstelle | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: 20d0fac68bb7cdb3d7f5cb6aac6b0ab67e373c84
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
ms.locfileid: "24726570"
---
# <a name="idebugapplicationnodeevents-interface"></a>IDebugApplicationNodeEvents-Schnittstelle
Stellt die Schnittstelle für die `IDebugApplicationNode` Schnittstelle.  
  
 Zusätzlich zu den von geerbten Methoden `IUnknown`, `IDebugApplicationNodeEvents` Schnittstelle macht die folgenden Methoden verfügbar.  
  
## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge  
  
|Methode|Beschreibung|  
|------------|-----------------|  
|[IDebugApplicationNodeEvents::onAddChild](../../winscript/reference/idebugapplicationnodeevents-onaddchild.md)|Behandelt das Ereignis, wenn ein Debug-Anwendungsobjekt Knoten ein untergeordneter Knoten hinzugefügt wird.|  
|[IDebugApplicationNodeEvents::onRemoveChild](../../winscript/reference/idebugapplicationnodeevents-onremovechild.md)|Behandelt das Ereignis, wenn ein untergeordneter Knoten vom Knotenobjekt für eine Debug-Anwendung entfernt wird.|  
|[IDebugApplicationNodeEvents::onDetach](../../winscript/reference/idebugapplicationnodeevents-ondetach.md)|Behandelt ein Ereignis gibt an, dass das Debug-Anwendungsobjekt Knoten von einem übergeordneten Knoten getrennt wurde.|  
|[IDebugApplicationNodeEvents::onAttach](../../winscript/reference/idebugapplicationnodeevents-onattach.md)|Behandelt ein Ereignis gibt an, dass das Debug-Anwendungsobjekt Knoten zu einem übergeordneten Knoten angefügt wurde.|  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugApplicationNode-Schnittstelle](../../winscript/reference/idebugapplicationnode-interface.md)