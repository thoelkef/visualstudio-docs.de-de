---
title: IActiveScriptStats-Schnittstelle | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IActiveScriptStats interface
ms.assetid: dbe84d6f-1b77-4877-aced-cd4e01ead5b5
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: da69920ca78ad47e283fa8f99a28d037edbbe44d
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/16/2019
ms.locfileid: "54350140"
---
# <a name="iactivescriptstats-interface"></a>IActiveScriptStats-Schnittstelle
Ermöglicht es einem Host zum Abfragen der Statistiken eines ausgeführten Skripts ein. Der Host kann diese Informationen verwenden, um zu bestimmen, ob das Skript zu lange dauernde stattgefunden hat.  
  
 Zusätzlich zu den von geerbten Methoden `IUnknown`, `IActiveScriptStats` Schnittstelle verfügbar macht, die folgenden Methoden.  
  
## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge  
  
|Methode|Beschreibung|  
|------------|-----------------|  
|[IActiveScriptStats::GetStat](../../winscript/reference/iactivescriptstats-getstat.md)|Gibt einen von der standard-Skripterstellung für Statistiken.|  
|[IActiveScriptStats::GetStatEx](../../winscript/reference/iactivescriptstats-getstatex.md)|Gibt eine benutzerdefiniertes Skript für Statistik zurück.|  
|[IActiveScriptStats::ResetStats](../../winscript/reference/iactivescriptstats-resetstats.md)|Setzt die Statistik für dieses Skript.|