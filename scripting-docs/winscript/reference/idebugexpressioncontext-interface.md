---
title: IDebugExpressionContext-Schnittstelle | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IDebugExpressionContext Interface
apilocation: jscript.dll
helpviewer_keywords: IDebugExpressionContext interface
ms.assetid: 52af82e8-0dec-49e2-a7f3-d00f66ca1401
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0c55a2f270e4c82c578450092e5066b19fe9e606
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="idebugexpressioncontext-interface"></a>IDebugExpressionContext-Schnittstelle
Stellt einen Kontext, in dem Ausdrücke ausgewertet werden kann. Die Stack-Frame-Objekt implementiert diese Schnittstelle.  
  
 Zusätzlich zu den von geerbten Methoden `IUnknown`, `IDebugExpressionContext` Schnittstelle macht die folgenden Methoden verfügbar.  
  
## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge  
  
|Methode|Beschreibung|  
|------------|-----------------|  
|[IDebugExpressionContext::ParseLanguageText](../../winscript/reference/idebugexpressioncontext-parselanguagetext.md)|Erstellt einen Debug-Ausdruck für den angegebenen Text.|  
|[IDebugExpressionContext::GetLanguageInfo](../../winscript/reference/idebugexpressioncontext-getlanguageinfo.md)|Gibt einen Namen und eine GUID für die Sprache, die diesem Kontext besitzt.|