---
title: Errorresumeaction-Enumeration | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- ERRORRESUMEACTION
apilocation:
- scrobj.dll
helpviewer_keywords:
- ERRORRESUMEACTION enumeration
ms.assetid: a68293c8-056b-439f-83e7-69e4a38f4976
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ad9b8598cb027c96f6fb6fad6f3d343e6058cfdb
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575861"
---
# <a name="errorresumeaction-enumeration"></a>ERRORRESUMEACTIONS-Enumeration
Beschreibt, wie der Vorgang von einem Laufzeitfehler aus fortgesetzt wird.  
  
## <a name="syntax"></a>Syntax  
  
```cpp
typedef enum tagERRORRESUMEACTION {  
   ERRORRESUMEACTION_ReexecuteErrorStatement,  
   ERRORRESUMEACTION_AbortCallAndReturnErrorToCaller,  
   ERRORRESUMEACTION_SkipErrorStatement,  
} ERRORRESUMEACTION;  
```  
  
## <a name="members"></a>Member  
  
|Member|Beschreibung|  
|------------|-----------------|  
|ERRORRESUMEACTION_ReexecuteErrorStatement|Führt die Anweisung erneut aus, die den Fehler erzeugt hat.|  
|ERRORRESUMEACTION_AbortCallAndReturnErrorToCaller|Ermöglicht der Sprach-Engine, den Fehler zu behandeln.|  
|ERRORRESUMEACTION_SkipErrorStatement|Nimmt die Ausführung im Code nach der Anweisung an, die den Fehler erzeugt hat.|  
  
## <a name="see-also"></a>Siehe auch  
 [Konstanten, Enumerationen und Strukturen für Active Script-Debugger](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)