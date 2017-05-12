---
title: "IDebugExpressionContext-Schnittstelle | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugExpressionContext Interface
apilocation: jscript.dll
helpviewer_keywords: 
  - "IDebugExpressionContext-Schnittstelle"
ms.assetid: 52af82e8-0dec-49e2-a7f3-d00f66ca1401
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugExpressionContext-Schnittstelle
Stellt einen Kontext dar, in dem Ausdrücke ausgewertet werden können.  Das Stapelrahmenobjekt implementiert diese Schnittstelle.  
  
 Zusätzlich zu den von `IUnknown` geerbten Methoden macht die `IDebugExpressionContext`\-Schnittstelle die folgenden Methoden verfügbar.  
  
## Methoden in Vtable\-Reihenfolge  
  
|Methode|Description|  
|-------------|-----------------|  
|[IDebugExpressionContext::ParseLanguageText](../../winscript/reference/idebugexpressioncontext-parselanguagetext.md)|Erstellt eine Multithread\-DLL Ausdruck für den angegebenen Text.|  
|[IDebugExpressionContext::GetLanguageInfo](../../winscript/reference/idebugexpressioncontext-getlanguageinfo.md)|Gibt einen Namen und GUID für die Sprache zurück, die diesen Kontext besitzt.|