---
title: IDebugStackFrame-Schnittstelle | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDebugStackFrame interface
ms.assetid: e95c1b4f-17c1-490c-a56b-c25fa45d4822
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d8f645d6460ff15734348267b5138b1b6edea071
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/19/2019
ms.locfileid: "58149548"
---
# <a name="idebugstackframe-interface"></a>IDebugStackFrame-Schnittstelle
Stellt einen logischen Stapelrahmen im Threadstapel dar. Rufen Sie die `IDebugStackFrame::QueryInterface` Methode zum Abrufen der `IDebugExpressionContext` -Schnittstelle, die Ausdruck, ausdrucksauswertung und Überwachungen Windows ermöglicht.  
  
 Zusätzlich zu den von geerbten Methoden `IUnknown`, `IDebugStackFrame` Schnittstelle verfügbar macht, die folgenden Methoden.  
  
## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge  
  
|Methode|Beschreibung|  
|------------|-----------------|  
|[IDebugStackFrame::GetCodeContext](../../winscript/reference/idebugstackframe-getcodecontext.md)|Gibt zurück, der aktuelle Codekontext, die dem Stapelrahmen zugeordnet.|  
|[IDebugStackFrame::GetDescriptionString](../../winscript/reference/idebugstackframe-getdescriptionstring.md)|Gibt eine kurze oder lange Text Beschreibung des Stapelrahmens zurück.|  
|[IDebugStackFrame::GetLanguageString](../../winscript/reference/idebugstackframe-getlanguagestring.md)|Gibt eine kurze oder lange Text Beschreibung der Sprache zurück.|  
|[IDebugStackFrame::GetThread](../../winscript/reference/idebugstackframe-getthread.md)|Gibt die Threads mit Stapelrahmen zurück.|  
|[IDebugStackFrame::GetDebugProperty](../../winscript/reference/idebugstackframe-getdebugproperty.md)|Gibt einen Eigenschaftenbrowser für den aktuellen Frame zurück.|