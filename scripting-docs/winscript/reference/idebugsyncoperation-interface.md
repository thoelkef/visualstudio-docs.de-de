---
title: IDebugSyncOperation-Schnittstelle | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDebugSyncOperation interface
ms.assetid: 8d714492-1836-462c-980a-c99e91a2c81b
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3724ad50771ca49460e130bf93ebc244681bd782
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/16/2019
ms.locfileid: "54349601"
---
# <a name="idebugsyncoperation-interface"></a>IDebugSyncOperation-Schnittstelle
Ermöglicht eine Skript-Engine, um einen Vorgang (z. B. die Auswertung des Ausdrucks) zu abstrahieren, die ausgeführt werden, während in einen bestimmten blockierten Thread geschachtelt. Die Schnittstelle bietet außerdem einen Mechanismus zum Abbrechen von nicht reagierender Vorgängen.  
  
 Zusätzlich zu den von geerbten Methoden `IUnknown`, `IDebugSyncOperation` Schnittstelle verfügbar macht, die folgenden Methoden.  
  
## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge  
  
|Methode|Beschreibung|  
|------------|-----------------|  
|[IDebugSyncOperation::GetTargetThread](../../winscript/reference/idebugsyncoperation-gettargetthread.md)|Gibt den Zielthread für die Anwendung für diesen synchronen Vorgang zurück.|  
|[IDebugSyncOperation::Execute](../../winscript/reference/idebugsyncoperation-execute.md)|Synchron den Vorgang ausführt, und gibt.|  
|[IDebugSyncOperation::InProgressAbort](../../winscript/reference/idebugsyncoperation-inprogressabort.md)|Bricht eine laufende Operation auf einem anderen Thread ab.|