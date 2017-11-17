---
title: ERRORRESUMEACTIONS-Enumeration | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: ERRORRESUMEACTION
apilocation: scrobj.dll
helpviewer_keywords: ERRORRESUMEACTION enumeration
ms.assetid: a68293c8-056b-439f-83e7-69e4a38f4976
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 914c1d7aa4d2935ea94322ebd257f4135d79e9c0
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="errorresumeaction-enumeration"></a>ERRORRESUMEACTIONS-Enumeration
Beschreibt, wie der Vorgang von einem Laufzeitfehler aus fortgesetzt wird.  
  
## <a name="syntax"></a>Syntax  
  
```  
typedef enum tagERRORRESUMEACTION {  
   ERRORRESUMEACTION_ReexecuteErrorStatement,  
   ERRORRESUMEACTION_AbortCallAndReturnErrorToCaller,  
   ERRORRESUMEACTION_SkipErrorStatement,  
} ERRORRESUMEACTION;  
```  
  
## <a name="members"></a>Member  
  
|Member|Beschreibung|  
|------------|-----------------|  
|ERRORRESUMEACTION_ReexecuteErrorStatement|Führt erneut die Anweisung, die den Fehler verursacht hat.|  
|ERRORRESUMEACTION_AbortCallAndReturnErrorToCaller|Ermöglicht das Sprachmodul, die den Fehler zu behandeln.|  
|ERRORRESUMEACTION_SkipErrorStatement|Setzt die Ausführung im Code nach der Anweisung, die den Fehler verursacht hat.|  
  
## <a name="see-also"></a>Siehe auch  
 [Konstanten, Enumerationen und Strukturen für Active Script-Debugger](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)