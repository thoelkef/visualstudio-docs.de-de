---
title: IDebugApplicationThread-Schnittstelle | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- IDebugApplicationThread interface
ms.assetid: f869c328-4409-4b74-a6c3-9e63fc58c63d
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6e731ba866504c9a3c3c9ad081a90a12b161355d
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="idebugapplicationthread-interface"></a>IDebugApplicationThread-Schnittstelle
Ermöglicht das Sprache-Module und Hosts Threadsynchronisierung bereitstellen und Verwalten von Status für threadspezifische Debuginformationen. Diese Schnittstelle erweitert die `IRemoteDebugApplicationThread` Schnittstelle, um nicht-Remote-Zugriff auf den Thread bereitzustellen.  
  
 Zusätzlich zu den von geerbten Methoden `IRemoteDebugApplicationThread`, `IDebugApplicationThread` Schnittstelle macht die folgenden Methoden verfügbar.  
  
## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge  
  
|Methode|Beschreibung|  
|------------|-----------------|  
|[IDebugApplicationThread::SynchronousCallIntoThread](../../winscript/reference/idebugapplicationthread-synchronouscallintothread.md)|Bietet einen Mechanismus für den Aufrufer Code im Thread Anwendung auszuführen.|  
|[IDebugApplicationThread::QueryIsCurrentThread](../../winscript/reference/idebugapplicationthread-queryiscurrentthread.md)|Bestimmt, ob der Thread den derzeit ausgeführten Thread ist.|  
|[IDebugApplicationThread::QueryIsDebuggerThread](../../winscript/reference/idebugapplicationthread-queryisdebuggerthread.md)|Bestimmt, ob dieser Thread Debugger ist.|  
|[IDebugApplicationThread::SetDescription](../../winscript/reference/idebugapplicationthread-setdescription.md)|Legt die Beschreibung dieser Thread fest.|  
|[IDebugApplicationThread::SetStateString](../../winscript/reference/idebugapplicationthread-setstatestring.md)|Legt die Beschreibung des Zustands Thread fest.|