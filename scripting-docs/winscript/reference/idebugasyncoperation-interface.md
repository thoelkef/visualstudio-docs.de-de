---
title: IDebugAsyncOperation-Schnittstelle | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- IDebugAsyncOperation interface
ms.assetid: ebb2ea75-1443-4d8a-812d-171a166f5f9d
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 157ed1248535855fcb53ca2eb6f49427fea94149
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="idebugasyncoperation-interface"></a>IDebugAsyncOperation-Schnittstelle
Der Debug-Prozess-Manager implementiert den `IDebugAsyncOperation` Schnittstelle. Ruft eine Sprachmodul die `IDebugApplication::CreateAsyncDebugOperation` Methode, um einen Verweis auf diese Schnittstelle abzurufen. Das Sprachmodul können die `IDebugAsyncOperation` Schnittstelle, um asynchroner Zugriff auf einen Vorgang synchron Debugmodus bereitzustellen.  
  
 Zusätzlich zu den von geerbten Methoden `IUnknown`, `IDebugAsyncOperation` Schnittstelle macht die folgenden Methoden verfügbar.  
  
## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge  
  
|Methode|Beschreibung|  
|------------|-----------------|  
|[IDebugAsyncOperation::GetSyncDebugOperation](../../winscript/reference/idebugasyncoperation-getsyncdebugoperation.md)|Gibt diesem Objekt zugeordneten synchron Debugmodus Vorgangs zurück.|  
|[IDebugAsyncOperation::Start](../../winscript/reference/idebugasyncoperation-start.md)|Bewirkt, dass den asynchronen Vorgang beginnen.|  
|[IDebugAsyncOperation::Abort](../../winscript/reference/idebugasyncoperation-abort.md)|Abbrechen eines Vorgangs an.|  
|[IDebugAsyncOperation::QueryIsComplete](../../winscript/reference/idebugasyncoperation-queryiscomplete.md)|Bestimmt, ob der Debugvorgang abgeschlossen wurde.|  
|[IDebugAsyncOperation::GetResult](../../winscript/reference/idebugasyncoperation-getresult.md)|Stellt den Rückgabewert und Rückgabeobjekt Parameter aus dem synchronen Debugvorgang.|