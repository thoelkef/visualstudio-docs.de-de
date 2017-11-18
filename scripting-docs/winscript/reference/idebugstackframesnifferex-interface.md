---
title: IDebugStackFrameSnifferEx-Schnittstelle | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords: IDebugStackFrameSnifferEx interface
ms.assetid: fd6cf744-dee7-45f2-9a90-355b90372923
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 56d6e63c41db274634b2593989800ea0392b93a6
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="idebugstackframesnifferex-interface"></a>IDebugStackFrameSnifferEx-Schnittstelle
Bietet eine Möglichkeit zum Auflisten der logischen Stapelrahmen, der von einer Komponente bezeichnet. Script-Module in der Regel implementieren Sie diese Schnittstelle. Der Prozess Debug-Manager verwendet diese Schnittstelle, um alle Stapelrahmen finden, die ein bestimmter Thread zugeordnet ist.  
  
> [!NOTE]
>  Diese Schnittstelle wird von innerhalb des relevanten Threads aufgerufen. Die Implementierung muss identifizieren den aktuellen Thread und einen entsprechenden Enumerator zurückgegeben.  
  
 Zusätzlich zu den von geerbten Methoden `IDebugStackFrameSniffer`, `IDebugStackFrameSnifferEx` Schnittstelle macht die folgenden Methoden verfügbar.  
  
## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge  
  
|Methode|Beschreibung|  
|------------|-----------------|  
|[IDebugStackFrameSnifferEx::EnumStackFramesEx](../../winscript/reference/idebugstackframesnifferex-enumstackframesex.md)|Gibt einen Enumerator für Stapelrahmen des aktuellen Threads zurück.|