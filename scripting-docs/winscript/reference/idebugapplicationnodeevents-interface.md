---
title: IDebugApplicationNodeEvents-Schnittstelle | Microsoft-Dokumentation
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
ms.openlocfilehash: 0396ed90437a98c8ee398f3c3acb0aeb5ddc77e2
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/16/2019
ms.locfileid: "54348411"
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