---
title: IDebugApplicationNode-Schnittstelle | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDebugApplicationNode interface
ms.assetid: 30be3a97-8191-45ac-8706-3f7056c163d6
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9be864fdb9468668633322066bbbcf11569e4eb3
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62822424"
---
# <a name="idebugapplicationnode-interface"></a>IDebugApplicationNode-Schnittstelle
Die `IDebugApplicationNode` Schnittstelle erweitert die Funktionalität der `IDebugDocumentProvider` -Schnittstelle durch die Bereitstellung eines Kontexts innerhalb einer Projektstruktur.  
  
 Zusätzlich zu den von geerbten Methoden `IDebugDocumentProvider`, `IDebugApplicationNode` Schnittstelle verfügbar macht, die folgenden Methoden.  
  
## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge  
  
|Methode|Beschreibung|  
|------------|-----------------|  
|[IDebugApplicationNode::EnumChildren](../../winscript/reference/idebugapplicationnode-enumchildren.md)|Listet die untergeordneten Knoten dieses Knotens für die Anwendung an.|  
|[IDebugApplicationNode::GetParent](../../winscript/reference/idebugapplicationnode-getparent.md)|Gibt den übergeordneten Knoten dieses Knotens für die Anwendung zurück.|  
|[IDebugApplicationNode::SetDocumentProvider](../../winscript/reference/idebugapplicationnode-setdocumentprovider.md)|Legt den Dokument-Anbieter für diesen Anwendungsknoten fest.|  
|[IDebugApplicationNode::Close](../../winscript/reference/idebugapplicationnode-close.md)|Bewirkt, dass dieser Anwendung alle Verweise freigeben, und geben einen inaktiven Status.|  
|[IDebugApplicationNode::Attach](../../winscript/reference/idebugapplicationnode-attach.md)|Der angegebene Projektstruktur wird dieser Anwendungsknoten hinzugefügt.|  
|[IDebugApplicationNode::Detach](../../winscript/reference/idebugapplicationnode-detach.md)|Entfernt diesen Anwendungsknoten aus der Projektstruktur an.|