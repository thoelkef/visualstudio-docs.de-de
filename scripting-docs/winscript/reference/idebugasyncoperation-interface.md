---
title: IDebugAsyncOperation-Schnittstelle | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDebugAsyncOperation interface
ms.assetid: ebb2ea75-1443-4d8a-812d-171a166f5f9d
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 820ecc40924ace4153b76f46c8b8fd1603512ebb
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/19/2019
ms.locfileid: "58150815"
---
# <a name="idebugasyncoperation-interface"></a>IDebugAsyncOperation-Schnittstelle
Implementiert den prozessbasierten Debugmanager der `IDebugAsyncOperation` Schnittstelle. Eine Sprach-Engine Ruft die `IDebugApplication::CreateAsyncDebugOperation` Methode, um einen Verweis auf diese Schnittstelle abzurufen. Die Sprach-Engine können die `IDebugAsyncOperation` Schnittstelle, um asynchronen Zugriff auf einen synchronen Debugvorgang bereitzustellen.  
  
 Zusätzlich zu den von geerbten Methoden `IUnknown`, `IDebugAsyncOperation` Schnittstelle verfügbar macht, die folgenden Methoden.  
  
## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge  
  
|Methode|Beschreibung|  
|------------|-----------------|  
|[IDebugAsyncOperation::GetSyncDebugOperation](../../winscript/reference/idebugasyncoperation-getsyncdebugoperation.md)|Gibt zurück, der diesem Objekt zugeordneten synchronen Debugvorgang.|  
|[IDebugAsyncOperation::Start](../../winscript/reference/idebugasyncoperation-start.md)|Bewirkt, dass den asynchronen Vorgang, um zu beginnen.|  
|[IDebugAsyncOperation::Abort](../../winscript/reference/idebugasyncoperation-abort.md)|Abbrechen eines Vorgangs an.|  
|[IDebugAsyncOperation::QueryIsComplete](../../winscript/reference/idebugasyncoperation-queryiscomplete.md)|Bestimmt, ob der Debugvorgang abgeschlossen wurde.|  
|[IDebugAsyncOperation::GetResult](../../winscript/reference/idebugasyncoperation-getresult.md)|Stellt den Rückgabewert und ein Rückgabeobjekt-Parameter aus der synchronen Debugvorgang.|