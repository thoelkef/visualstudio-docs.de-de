---
title: IDebugStackFrameSnifferEx-Schnittstelle | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDebugStackFrameSnifferEx interface
ms.assetid: fd6cf744-dee7-45f2-9a90-355b90372923
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: dc6e892c00a2d86e784857f08772550897e1ec4e
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/19/2019
ms.locfileid: "58157123"
---
# <a name="idebugstackframesnifferex-interface"></a>IDebugStackFrameSnifferEx-Schnittstelle
Bietet eine Möglichkeit zum Auflisten der logischen Stapelrahmen, der von einer Komponente bezeichnet. Skript-Engines werden in der Regel diese Schnittstelle implementieren. Die Debug-Manager verwendet diese Schnittstelle, um alle Stapelrahmen zu finden, die ein bestimmter Thread zugeordnet ist.  
  
> [!NOTE]
>  Diese Schnittstelle wird von innerhalb des relevanten Threads aufgerufen werden. Die Implementierung muss identifiziert den aktuellen Thread und einen entsprechenden Enumerator zurückgeben.  
  
 Zusätzlich zu den von geerbten Methoden `IDebugStackFrameSniffer`, `IDebugStackFrameSnifferEx` Schnittstelle verfügbar macht, die folgenden Methoden.  
  
## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge  
  
|Methode|Beschreibung|  
|------------|-----------------|  
|[IDebugStackFrameSnifferEx::EnumStackFramesEx](../../winscript/reference/idebugstackframesnifferex-enumstackframesex.md)|Gibt einen Enumerator der Stapelrahmen des aktuellen Threads.|