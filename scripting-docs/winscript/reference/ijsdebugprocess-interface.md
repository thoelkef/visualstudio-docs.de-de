---
title: IJsDebugProcess-Schnittstelle | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: a7ad5525-55b7-4c68-a4f7-c508f7877712
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 411679a03daf27046fdcede7ff48e76212bbd2fd
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62557945"
---
# <a name="ijsdebugprocess-interface"></a>IJsDebugProcess-Schnittstelle
Stellt Routinen zum Überprüfen und Steuern des Zielprozesses bereit.  
  
## <a name="syntax"></a>Syntax  
  
```cpp
IJsDebugProcess : public IUnknown;  
```  
  
## <a name="members"></a>Member  
  
### <a name="public-methods"></a>Öffentliche Methoden  
  
|Name|Beschreibung|  
|----------|-----------------|  
|[IJsDebugProcess::CreateBreakPoint-Methode](../../winscript/reference/ijsdebugprocess-createbreakpoint-method.md)|Legt den Haltepunkt an der angegebenen Dokumentposition fest.|  
|[IJsDebugProcess::CreateStackWalker-Methode](../../winscript/reference/ijsdebugprocess-createstackwalker-method.md)|Factorymethode für Stapeldurchlauf.|  
|[IJsDebugProcess::PerformAsyncBreak-Methode](../../winscript/reference/ijsdebugprocess-performasyncbreak-method.md)|Setzt die Skript-Engine in den Unterbrechungsmodus, der bei der nächsten Skriptanweisung eine Unterbrechung veranlasst.|  
  
## <a name="requirements"></a>Anforderungen  
 **Header:** "jscript9diag.h"  
  
## <a name="see-also"></a>Siehe auch  
 [Windows Script-Schnittstellenreferenz](../../winscript/reference/windows-script-interfaces-reference.md)