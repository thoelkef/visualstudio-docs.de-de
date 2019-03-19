---
title: IDebugApplicationNode100-Schnittstelle | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDebugApplicationNode100 Interface
ms.assetid: 43966d4e-5f89-4a04-a08d-782347d00c2d
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f380245422047142b3f06757f6c1057302dd5d26
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/19/2019
ms.locfileid: "58146044"
---
# <a name="idebugapplicationnode100-interface"></a>IDebugApplicationNode100-Schnittstelle
Die `IDebugApplicationNode100` Schnittstelle erweitert die Funktionalität der [IDebugApplicationNode-Schnittstelle](../../winscript/reference/idebugapplicationnode-interface.md). Sie können eine Instanz dieser Schnittstelle abrufen, indem Sie QueryInterface aufrufen, bei der Implementierung der [IDebugApplicationNode-Schnittstelle](../../winscript/reference/idebugapplicationnode-interface.md).  
  
> [!IMPORTANT]
>  Diese Schnittstelle wird von PDM v10. 0 und höher implementiert. Gefunden in activdbg100.h.  
  
## <a name="methods"></a>Methoden  
 Die `IDebugApplicationNode100`-Schnittstelle macht die folgenden Methoden verfügbar:  
  
|Methode|Beschreibung|  
|------------|-----------------|  
|[IDebugApplicationNode100::GetExcludedDocuments](../../winscript/reference/idebugapplicationnode100-getexcludeddocuments.md)|Ruft ab, der Textdokumente, die vom angegebenen Filter ausgeblendet sind.|  
|[IDebugApplicationNode100::QueryIsChildNode](../../winscript/reference/idebugapplicationnode100-queryischildnode.md)|Bestimmt, ob das angegebene Dokument zu einem der untergeordneten Knoten dieses Knotens gehört.|  
|[IDebugApplicationNode100::SetFilterForEventSink](../../winscript/reference/idebugapplicationnode100-setfilterforeventsink.md)|Legt den Filter für eine bestimmte [IDebugApplicationNodeEvents-Schnittstelle](../../winscript/reference/idebugapplicationnodeevents-interface.md) Implementierung. Sie können die Skriptdebugger, um vom Compiler generierten untergeordneten Anwendungsknoten zu filtern, damit das PDM mehr senden, werden Ereignisse aus, wenn die Knoten erstellt oder entfernt werden. Standardmäßig werden alle Knoten gesendet.|