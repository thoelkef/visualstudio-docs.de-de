---
title: IActiveScriptStats-Schnittstelle | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- IActiveScriptStats interface
ms.assetid: dbe84d6f-1b77-4877-aced-cd4e01ead5b5
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d459b89bde609dfdf5963d4b6b10b24db4706a7e
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptstats-interface"></a>IActiveScriptStats-Schnittstelle
Ermöglicht es einem Host die Statistik von einem ausgeführten Skript abgefragt. Der Host kann diese Informationen verwenden, um festzustellen, ob das Skript zu lange gedauert hat.  
  
 Zusätzlich zu den von geerbten Methoden `IUnknown`, `IActiveScriptStats` Schnittstelle macht die folgenden Methoden verfügbar.  
  
## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge  
  
|Methode|Beschreibung|  
|------------|-----------------|  
|[IActiveScriptStats::GetStat](../../winscript/reference/iactivescriptstats-getstat.md)|Gibt einen der Standardskripts Statistiken zurück.|  
|[IActiveScriptStats::GetStatEx](../../winscript/reference/iactivescriptstats-getstatex.md)|Gibt eine benutzerdefiniertes Skript Statistik zurück.|  
|[IActiveScriptStats::ResetStats](../../winscript/reference/iactivescriptstats-resetstats.md)|Setzt die Statistik für dieses Skript.|