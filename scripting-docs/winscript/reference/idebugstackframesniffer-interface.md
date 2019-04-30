---
title: IDebugStackFrameSniffer-Schnittstelle | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDebugStackFrameSniffer interface
ms.assetid: 5669598e-a6bd-4694-9cb2-bd908be72bed
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5c9181b5013a9584a2a686ed0e499698be0b62b9
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63432258"
---
# <a name="idebugstackframesniffer-interface"></a>IDebugStackFrameSniffer-Schnittstelle
Bietet eine Möglichkeit zum Auflisten der logischen Stapelrahmen, der von einer Komponente bezeichnet. Skript-Engines werden in der Regel diese Schnittstelle implementieren. Die Debug-Manager verwendet diese Schnittstelle, um alle Stapelrahmen zu finden, die ein bestimmter Thread zugeordnet ist.  
  
> [!NOTE]
> Der Debugger ruft dieser Schnittstelle vom innerhalb des Threads von Interesse sind. Die Skript-Engine muss identifiziert den aktuellen Thread und einen entsprechenden Enumerator zurückgeben.  
  
## <a name="methods"></a>Methoden  
 Zusätzlich zu den von geerbten Methoden `IUnknown`, `IDebugStackFrameSniffer` Schnittstelle verfügbar macht, die folgenden Methoden.  
  
|Methode|Beschreibung|  
|------------|-----------------|  
|[IDebugStackFrameSniffer::EnumStackFrames](../../winscript/reference/idebugstackframesniffer-enumstackframes.md)|Gibt einen Enumerator der Stapelrahmen des aktuellen Threads.|