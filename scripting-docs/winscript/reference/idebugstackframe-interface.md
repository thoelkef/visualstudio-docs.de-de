---
title: IDebugStackFrame-Schnittstelle | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords: IDebugStackFrame interface
ms.assetid: e95c1b4f-17c1-490c-a56b-c25fa45d4822
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 36fa0ba2d1b4049ad41ff0502ed33be0a706d9f6
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="idebugstackframe-interface"></a>IDebugStackFrame-Schnittstelle
Stellt einen logischen Stapelrahmen im Stapel Thread dar. Rufen Sie die `IDebugStackFrame::QueryInterface` Methode zum Abrufen der `IDebugExpressionContext` -Schnittstelle, die Ausdruck Auswertung "und" Überwachen von Windows ermöglicht.  
  
 Zusätzlich zu den von geerbten Methoden `IUnknown`, `IDebugStackFrame` Schnittstelle macht die folgenden Methoden verfügbar.  
  
## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge  
  
|Methode|Beschreibung|  
|------------|-----------------|  
|[IDebugStackFrame::GetCodeContext](../../winscript/reference/idebugstackframe-getcodecontext.md)|Gibt den Stapelrahmen zugeordneten Codekontext zurück.|  
|[IDebugStackFrame::GetDescriptionString](../../winscript/reference/idebugstackframe-getdescriptionstring.md)|Gibt eine kurze oder lange Text Beschreibung des Stapelrahmens zurück.|  
|[IDebugStackFrame::GetLanguageString](../../winscript/reference/idebugstackframe-getlanguagestring.md)|Gibt eine kurze oder lange Text Beschreibung der Sprache zurück.|  
|[IDebugStackFrame::GetThread](../../winscript/reference/idebugstackframe-getthread.md)|Gibt den Thread zugeordnete dieses Stapelrahmens zurück.|  
|[IDebugStackFrame::GetDebugProperty](../../winscript/reference/idebugstackframe-getdebugproperty.md)|Gibt einen Eigenschaftenbrowser für den aktuellen Frame zurück.|