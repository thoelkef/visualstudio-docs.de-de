---
title: IDebugExpressionContext-Schnittstelle | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugExpressionContext Interface
apilocation:
- jscript.dll
helpviewer_keywords:
- IDebugExpressionContext interface
ms.assetid: 52af82e8-0dec-49e2-a7f3-d00f66ca1401
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5920d644922b15f193ee396ea0c6bddb8a574698
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62996878"
---
# <a name="idebugexpressioncontext-interface"></a>IDebugExpressionContext-Schnittstelle
Stellt einen Kontext, in dem Ausdrücke ausgewertet werden können. Das Stack-Frame-Objekt implementiert diese Schnittstelle.  
  
 Zusätzlich zu den von geerbten Methoden `IUnknown`, `IDebugExpressionContext` Schnittstelle verfügbar macht, die folgenden Methoden.  
  
## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge  
  
|Methode|Beschreibung|  
|------------|-----------------|  
|[IDebugExpressionContext::ParseLanguageText](../../winscript/reference/idebugexpressioncontext-parselanguagetext.md)|Erstellt einen Debug-Ausdruck für den angegebenen Text.|  
|[IDebugExpressionContext::GetLanguageInfo](../../winscript/reference/idebugexpressioncontext-getlanguageinfo.md)|Gibt einen Namen und eine GUID zurück, für die Sprache, die diesem Kontext besitzt.|