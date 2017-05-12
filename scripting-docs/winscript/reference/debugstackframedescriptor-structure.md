---
title: "DebugStackFrameDescriptor-Struktur | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: DebugStackFrameDescriptor
apilocation: scrobj.dll
helpviewer_keywords: 
  - "DebugStackFrameDescriptor-Struktur"
ms.assetid: a86bcb99-41e4-4a26-a1dd-e1458fb73139
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# DebugStackFrameDescriptor-Struktur
Listet Stapelrahmen auf und Zusammenführungsausgabe von einigen Enumeratoren auf den Thread aufruft.  
  
## Syntax  
  
```  
typedef struct tagDebugStackFrameDescriptor {  
   IDebugStackFrame *pdsf;  
   DWORD_PTR        dwMin;  
   DWORD_PTR        dwLim;  
   BOOL             fFinal;  
   IUnknown         *punkFinal;  
} DebugStackFrameDescriptor;  
```  
  
## Mitglieder  
 `pdsf`  
 Das Stapelrahmenobjekt.  
  
 `dwMin`  
 Eine Darstellung des Elements Computerabhängigen des unteren Bereich der physischen Adressen zugeordnet mit diesem Stapelrahmen.  
  
 `dwLim`  
 Eine Darstellung des Elements Computerabhängigen des oberen Bereich der physischen Adressen zugeordnet mit diesem Stapelrahmen.  
  
 `fFinal`  
 Kennzeichnen, das angibt, dass die Frames verarbeitet werden.  
  
 `punkFinal`  
 Wenn dieser Parameter nicht `NULL` ist, sollte das aktuelle Enumeratorzusammenführen beendet und ein neues sollte gestartet werden.  Das Objekt gibt an, wie die neue Enumeration beginnt.  
  
## Hinweise  
 Der Debug\- ProzessManager verwendet diese Struktur sortieren, wenn die Stapelrahmen aus mehreren Skriptmodulen.  Gemäß der Konvention wachsen Stapel unten.  Daher auf Dokumente, in denen Stapel heranwachsen, sollten die Adressen twos\-ergänztwerden.  
  
## Siehe auch  
 [Konstanten, Enumerationen und Strukturen für Active Script\-Debugger](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)