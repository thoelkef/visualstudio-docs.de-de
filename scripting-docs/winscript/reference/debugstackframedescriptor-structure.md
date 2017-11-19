---
title: DebugStackFrameDescriptor-Struktur | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: DebugStackFrameDescriptor
apilocation: scrobj.dll
helpviewer_keywords: DebugStackFrameDescriptor structure
ms.assetid: a86bcb99-41e4-4a26-a1dd-e1458fb73139
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 346f039ca96f2160d7ac28686e542b3d88a91dfb
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="debugstackframedescriptor-structure"></a>DebugStackFrameDescriptor-Struktur
Listet Stapelrahmen auf und fügt die Ausgabe mehrerer Enumeratoren in demselben Thread zusammen.  
  
## <a name="syntax"></a>Syntax  
  
```  
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
 Die Stack-Frame-Objekts.  
  
 `dwMin`  
 Eine rechnerabhängige-Darstellung der den unteren Bereich der physischen Adressen dieses Stapelrahmens zugeordnet werden soll.  
  
 `dwLim`  
 Eine rechnerabhängige-Darstellung des oberen Bereichs der physischen Adressen dieses Stapelrahmens zugeordnet werden soll.  
  
 `fFinal`  
 Flag, die angibt, dass der Frame gerade verarbeitet wird.  
  
 `punkFinal`  
 Wenn dieser Parameter nicht `NULL`, der aktuelle Enumerator Zusammenführen beendet werden soll, und eine neue gestartet werden soll. Das Objekt gibt an, wie die neue Enumeration zu starten.  
  
## <a name="remarks"></a>Hinweise  
 Der Prozess-Manager verwendet diese Struktur, um den Stapelrahmen aus mehreren Script-Module zu sortieren. Gemäß der Konvention wachsen Stapel nach unten aus. Daher sollte an Architekturen, auf dem Stapel wächst, die Adressen zweit ergänzt sein.  
  
## <a name="see-also"></a>Siehe auch  
 [Konstanten, Enumerationen und Strukturen für Active Script-Debugger](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)