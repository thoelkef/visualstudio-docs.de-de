---
title: DebugStackFrameDescriptor-Struktur | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- DebugStackFrameDescriptor
apilocation:
- scrobj.dll
helpviewer_keywords:
- DebugStackFrameDescriptor structure
ms.assetid: a86bcb99-41e4-4a26-a1dd-e1458fb73139
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: fddae48178ec6c56ce647f5c4f3a1bff3d81a980
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/19/2019
ms.locfileid: "58153317"
---
# <a name="debugstackframedescriptor-structure"></a>DebugStackFrameDescriptor-Struktur
Listet Stapelrahmen auf und fügt die Ausgabe mehrerer Enumeratoren in demselben Thread zusammen.  
  
## <a name="syntax"></a>Syntax  
  
```cpp
typedef struct tagDebugStackFrameDescriptor {  
   IDebugStackFrame *pdsf;  
   DWORD_PTR        dwMin;  
   DWORD_PTR        dwLim;  
   BOOL             fFinal;  
   IUnknown         *punkFinal;  
} DebugStackFrameDescriptor;  
```  
  
## <a name="members"></a>Member  
 `pdsf`  
 Das Stack-Frame-Objekt.  
  
 `dwMin`  
 Eine abhängig vom Computer-Darstellung, der den unteren Bereich der physischen Adressen, die diesen Stapelrahmen zugeordnet werden soll.  
  
 `dwLim`  
 Eine abhängig vom Computer-Darstellung der obere Bereich von physischen Adressen, die diesen Stapelrahmen zugeordnet werden soll.  
  
 `fFinal`  
 Flag, das zeigt an, dass der Rahmen verarbeitet wird.  
  
 `punkFinal`  
 Wenn dieser Parameter nicht `NULL`, wird der aktuelle Enumerator Zusammenführen beendet werden soll, und eine neue gestartet werden soll. Das Objekt gibt an, wie die neue Enumeration zu starten.  
  
## <a name="remarks"></a>Hinweise  
 Prozessbasierter Debug-Manager verwendet diese Struktur, um die Stapelrahmen von mehreren Skript-Engines zu sortieren. Wachsen gemäß der Konvention Stapel nach unten. Daher sollte auf Architekturen, in dem Stapel sich vergrößert, die Adressen 2er-ergänzt sein.  
  
## <a name="see-also"></a>Siehe auch  
 [Konstanten, Enumerationen und Strukturen für Active Script-Debugger](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)