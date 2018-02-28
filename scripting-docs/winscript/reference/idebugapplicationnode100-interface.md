---
title: IDebugApplicationNode100-Schnittstelle | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- IDebugApplicationNode100 Interface
ms.assetid: 43966d4e-5f89-4a04-a08d-782347d00c2d
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: af79614d38ef55776b660329f51931be70b7f52e
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="idebugapplicationnode100-interface"></a>IDebugApplicationNode100-Schnittstelle
Die `IDebugApplicationNode100` -Schnittstelle erweitert die Funktionalität der [IDebugApplicationNode-Schnittstelle](../../winscript/reference/idebugapplicationnode-interface.md). Sie erhalten eine Instanz dieser Schnittstelle durch den Aufruf von QueryInterface bei der Implementierung der [IDebugApplicationNode-Schnittstelle](../../winscript/reference/idebugapplicationnode-interface.md).  
  
> [!IMPORTANT]
>  Diese Schnittstelle wird von PDM v10. 0 und höher implementiert. Gefunden in activdbg100.h.  
  
## <a name="methods"></a>Methoden  
 Die `IDebugApplicationNode100`-Schnittstelle macht die folgenden Methoden verfügbar:  
  
|Methode|Beschreibung|  
|------------|-----------------|  
|[IDebugApplicationNode100::GetExcludedDocuments](../../winscript/reference/idebugapplicationnode100-getexcludeddocuments.md)|Ruft den Text-Dokumenten, die durch den angegebenen Filter ausgeblendet sind.|  
|[IDebugApplicationNode100::QueryIsChildNode](../../winscript/reference/idebugapplicationnode100-queryischildnode.md)|Bestimmt, ob das angegebene Dokument zu einem der untergeordneten Knoten dieses Knotens gehört.|  
|[IDebugApplicationNode100::SetFilterForEventSink](../../winscript/reference/idebugapplicationnode100-setfilterforeventsink.md)|Legt den Filter für eine bestimmte [IDebugApplicationNodeEvents-Schnittstelle](../../winscript/reference/idebugapplicationnodeevents-interface.md) Implementierung. Skriptdebugger, die vom Compiler generierte Anwendung Unterknoten herausfiltern, sodass die PDM nicht mehr senden, werden Ereignisse aus, wenn der Knoten erstellt oder entfernt werden können. Standardmäßig werden alle Knoten gesendet.|