---
title: IDebugApplicationThread-Schnittstelle | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDebugApplicationThread interface
ms.assetid: f869c328-4409-4b74-a6c3-9e63fc58c63d
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a464085eddbea4f5d29c684c0f1dabc6f853b6d1
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/19/2019
ms.locfileid: "58158788"
---
# <a name="idebugapplicationthread-interface"></a>IDebugApplicationThread-Schnittstelle
Ermöglicht Sprach-Engines und Hosts Threadsynchronisierung zu bieten und threadspezifische Zustand Debuginformationen zu verwalten. Diese Schnittstelle erweitert die `IRemoteDebugApplicationThread` Schnittstelle, um nicht-Remote-Zugriff auf den Thread bereitzustellen.  
  
 Zusätzlich zu den von geerbten Methoden `IRemoteDebugApplicationThread`, `IDebugApplicationThread` Schnittstelle verfügbar macht, die folgenden Methoden.  
  
## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge  
  
|Methode|Beschreibung|  
|------------|-----------------|  
|[IDebugApplicationThread::SynchronousCallIntoThread](../../winscript/reference/idebugapplicationthread-synchronouscallintothread.md)|Stellt einen Mechanismus für den Aufrufer, Code in dem Thread der Anwendung auszuführen.|  
|[IDebugApplicationThread::QueryIsCurrentThread](../../winscript/reference/idebugapplicationthread-queryiscurrentthread.md)|Bestimmt, ob der Thread den derzeit ausgeführten Thread ist.|  
|[IDebugApplicationThread::QueryIsDebuggerThread](../../winscript/reference/idebugapplicationthread-queryisdebuggerthread.md)|Bestimmt, ob dieser Thread Debugger ist.|  
|[IDebugApplicationThread::SetDescription](../../winscript/reference/idebugapplicationthread-setdescription.md)|Legt die Beschreibung dieses Threads fest.|  
|[IDebugApplicationThread::SetStateString](../../winscript/reference/idebugapplicationthread-setstatestring.md)|Legt die Beschreibung der der Zustand des Threads fest.|