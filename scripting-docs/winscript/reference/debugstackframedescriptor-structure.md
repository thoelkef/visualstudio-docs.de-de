---
title: Enbugstackframedescriptor-Struktur | Microsoft-Dokumentation
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
ms.openlocfilehash: 910e08ec6d9982354eb71b50d5e916917808f140
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/18/2019
ms.locfileid: "72576550"
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
 Das Stapel Rahmen Objekt.  
  
 `dwMin`  
 Eine Computer abhängige Darstellung des unteren Bereichs physischer Adressen, die diesem Stapel Rahmen zugeordnet ist.  
  
 `dwLim`  
 Eine Computer abhängige Darstellung des oberen Bereichs physischer Adressen, die diesem Stapel Rahmen zugeordnet ist.  
  
 `fFinal`  
 Flag, das angibt, dass der Frame verarbeitet wird.  
  
 `punkFinal`  
 Wenn dieser Parameter nicht `NULL` ist, sollte die aktuelle Zusammenführung des Enumerators angehalten und ein neuer Vorgang gestartet werden. Das-Objekt gibt an, wie die neue-Enumeration gestartet wird.  
  
## <a name="remarks"></a>Hinweise  
 Der Process Debug Manager verwendet diese Struktur zum Sortieren der Stapel Rahmen aus mehreren Skript-Engines. Gemäß der Konvention werden Stapel nach unten vergrößert. Folglich sollten bei Architekturen, in denen Stapel vergrößert werden, die Adressen durch Twos ergänzt werden.  
  
## <a name="see-also"></a>Siehe auch  
 [Konstanten, Enumerationen und Strukturen für Active Script-Debugger](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)