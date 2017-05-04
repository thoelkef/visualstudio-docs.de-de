---
title: "IDebugApplicationNode100-Schnittstelle | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IDebugApplicationNode100-Schnittstelle"
ms.assetid: 43966d4e-5f89-4a04-a08d-782347d00c2d
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# IDebugApplicationNode100-Schnittstelle
Die `IDebugApplicationNode100`\-Schnittstelle erweitert die Funktionalität [IDebugApplicationNode\-Schnittstelle](../../winscript/reference/idebugapplicationnode-interface.md).  Sie können eine Instanz dieser Schnittstelle abrufen, indem Sie entweder QueryInterface auf einer Implementierung von [IDebugApplicationNode\-Schnittstelle](../../winscript/reference/idebugapplicationnode-interface.md) aufrufen.  
  
> [!IMPORTANT]
>  Diese Schnittstelle wird von PDM v10.0 und höher implementiert.  Fundumgebung activdbg100.h.  
  
## Methoden  
 Die `IDebugApplicationNode100`\-Schnittstelle macht die folgenden Methoden verfügbar:  
  
|Methode|Description|  
|-------------|-----------------|  
|[IDebugApplicationNode100::GetExcludedDocuments](../../winscript/reference/idebugapplicationnode100-getexcludeddocuments.md)|Ruft die Textdokumente ab, die von den angegebenen Filter ausgeblendet werden.|  
|[IDebugApplicationNode100::QueryIsChildNode](../../winscript/reference/idebugapplicationnode100-queryischildnode.md)|Bestimmt, ob das angegebene Dokument auf einen der untergeordneten Knoten des Knotens gehört.|  
|[IDebugApplicationNode100::SetFilterForEventSink](../../winscript/reference/idebugapplicationnode100-setfilterforeventsink.md)|Legt den Filter auf einer bestimmten [IDebugApplicationNodeEvents\-Schnittstelle](../../winscript/reference/idebugapplicationnodeevents-interface.md) Implementierung fest.  Sie können Skriptdebuggern, um vom Compiler generierte untergeordnete Anwendungsknoten herauszufiltern, damit das PDM nicht mehr Ereignisse sendet, wenn die Knoten erstellt oder entfernt werden.  Standardmäßig werden alle Knoten gesendet.|