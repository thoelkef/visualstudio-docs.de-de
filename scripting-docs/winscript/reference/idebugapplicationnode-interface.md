---
title: IDebugApplicationNode-Schnittstelle | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords: IDebugApplicationNode interface
ms.assetid: 30be3a97-8191-45ac-8706-3f7056c163d6
caps.latest.revision: "9"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 110e04d1c990f1b22f9740d8118a47f485dd041e
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="idebugapplicationnode-interface"></a>IDebugApplicationNode-Schnittstelle
Die `IDebugApplicationNode` -Schnittstelle erweitert die Funktionalität von der `IDebugDocumentProvider` -Schnittstelle durch einen Kontext in einer Projektstruktur bereitstellt.  
  
 Zusätzlich zu den von geerbten Methoden `IDebugDocumentProvider`, `IDebugApplicationNode` Schnittstelle macht die folgenden Methoden verfügbar.  
  
## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge  
  
|Methode|Beschreibung|  
|------------|-----------------|  
|[IDebugApplicationNode::EnumChildren](../../winscript/reference/idebugapplicationnode-enumchildren.md)|Listet die untergeordneten Knoten dieses Knotens Anwendung an.|  
|[IDebugApplicationNode::GetParent](../../winscript/reference/idebugapplicationnode-getparent.md)|Der übergeordnete Knoten dieses Knotens Anwendung zurückgegeben.|  
|[IDebugApplicationNode::SetDocumentProvider](../../winscript/reference/idebugapplicationnode-setdocumentprovider.md)|Legt den Dokument-Anbieter für diesen Anwendungsknoten fest.|  
|[IDebugApplicationNode::Close](../../winscript/reference/idebugapplicationnode-close.md)|Bewirkt, dass diese Anwendung alle Verweise freigeben, und geben einen inaktiven Status.|  
|[IDebugApplicationNode::Attach](../../winscript/reference/idebugapplicationnode-attach.md)|Der angegebene Projektstruktur hinzugefügt dieser Anwendungsknoten.|  
|[IDebugApplicationNode::Detach](../../winscript/reference/idebugapplicationnode-detach.md)|Entfernt diesen Anwendungsknoten aus der Projektstruktur.|