---
title: SCRIPT_DEBUGGER_OPTIONS-Enumeration | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- SCRIPT_DEBUGGER_OPTIONS Enumeration
ms.assetid: aef41ec0-6f65-48e8-a69e-44b4e4fb929f
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c69d419732786442cda275bf85c74ab2b9d3e870
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/18/2019
ms.locfileid: "72574563"
---
# <a name="script_debugger_options-enumeration"></a>SCRIPT_DEBUGGER_OPTIONS-Enumeration
Gibt einen Satz von Optionen und/oder Funktionen an, die für den angefügten Debugger gelten. Wird in [IDebugApplicationNode100:: getexcludezddocuments](../../winscript/reference/idebugapplicationnode100-getexcludeddocuments.md) und [IDebugApplicationNode100:: setfilterforeventsink](../../winscript/reference/idebugapplicationnode100-setfilterforeventsink.md) verwendet.  
  
> [!IMPORTANT]
> Diese Konstanten werden von PDM v 10.0 und höher implementiert. Gefunden in activdbg100.h.  
  
## <a name="syntax"></a>Syntax  
  
```cpp
typedef SCRIPT_DEBUGGER_OPTIONS  
```  
  
## <a name="members"></a>Member  
  
|Member|Wert|Beschreibung|  
|------------|-----------|-----------------|  
|SDO_NONE|0x00000000|Es sind keine Optionen festgelegt.|  
|SDO_ENABLE_FIRST_CHANCE_EXCEPTIONS|0x00000001|Gibt an, dass die Skript Laufzeit BREAKREASON_ERROR-Ereignisse auslösen soll, wenn eine Ausnahme ausgelöst wird. Diese Option kann vom Debugger festgelegt oder durch Benutzercode über `Debug.enableFirstChanceExceptions(<true&#124;false>)` festgelegt werden.|  
|SDO_ENABLE_WEB_WORKER_SUPPORT|0x00000002|Gibt an, dass der angefügte Debugger Web-Worker unterstützt.|  
  
## <a name="see-also"></a>Siehe auch  
 [Konstanten, Enumerationen und Strukturen für Active Script-Debugger](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)