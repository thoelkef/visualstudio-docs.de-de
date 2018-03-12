---
title: IDebugSyncOperation-Schnittstelle | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- IDebugSyncOperation interface
ms.assetid: 8d714492-1836-462c-980a-c99e91a2c81b
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6705c2aa990aef3cf551a94546bf78a64026cecc
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="idebugsyncoperation-interface"></a>IDebugSyncOperation-Schnittstelle
Ermöglicht es, einen Vorgang (z. B. die Auswertung von Ausdrücken) zu abstrahieren, der ausgeführt werden, während in einem bestimmten blockierten Thread geschachtelt muss ein Skriptmodul. Die Schnittstelle bietet außerdem einen Mechanismus zum Abbrechen von Vorgängen nicht reagiert.  
  
 Zusätzlich zu den von geerbten Methoden `IUnknown`, `IDebugSyncOperation` Schnittstelle macht die folgenden Methoden verfügbar.  
  
## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge  
  
|Methode|Beschreibung|  
|------------|-----------------|  
|[IDebugSyncOperation::GetTargetThread](../../winscript/reference/idebugsyncoperation-gettargetthread.md)|Gibt den Zielthread für die Anwendung für diese synchron zurück.|  
|[IDebugSyncOperation::Execute](../../winscript/reference/idebugsyncoperation-execute.md)|Synchron führt den Vorgang, und gibt zurück.|  
|[IDebugSyncOperation::InProgressAbort](../../winscript/reference/idebugsyncoperation-inprogressabort.md)|Bricht eine laufende Operation auf einen anderen Thread ab.|