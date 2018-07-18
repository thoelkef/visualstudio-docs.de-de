---
title: IDebugStackFrameSniffer-Schnittstelle | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: 250c104d24f27900a6ff0eb8e8f72644f820bf5a
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
ms.locfileid: "24726800"
---
# <a name="idebugstackframesniffer-interface"></a>IDebugStackFrameSniffer-Schnittstelle
Bietet eine Möglichkeit zum Auflisten der logischen Stapelrahmen, der von einer Komponente bezeichnet. Script-Module in der Regel implementieren Sie diese Schnittstelle. Der Prozess Debug-Manager verwendet diese Schnittstelle, um alle Stapelrahmen finden, die ein bestimmter Thread zugeordnet ist.  
  
> [!NOTE]
>  Der Debugger ruft diese Benutzeroberfläche des Abfragegenerators innerhalb der Thread von Interesse sind. Das Skriptmodul muss identifizieren den aktuellen Thread und einen entsprechenden Enumerator zurückgegeben.  
  
## <a name="methods"></a>Methoden  
 Zusätzlich zu den von geerbten Methoden `IUnknown`, `IDebugStackFrameSniffer` Schnittstelle macht die folgenden Methoden verfügbar.  
  
|Methode|Beschreibung|  
|------------|-----------------|  
|[IDebugStackFrameSniffer::EnumStackFrames](../../winscript/reference/idebugstackframesniffer-enumstackframes.md)|Gibt einen Enumerator für Stapelrahmen des aktuellen Threads zurück.|