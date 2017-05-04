---
title: "JS_NATIVE_FRAME-Struktur | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: JS_NATIVE_FRAME
apilocation: jscript9diag.dll
ms.assetid: 5afa2ee1-b3e2-47cb-b304-84f96e6fbb14
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# JS_NATIVE_FRAME-Struktur
Stellt einen Stapelrahmen dar.  
  
## Syntax  
  
```  
typedef struct {  
    UINT64 InstructionOffset;  
    UINT64 ReturnOffset;  
    UINT64 FrameOffset;  
    UINT64 StackOffset;  
} JS_NATIVE_FRAME;  
```  
  
## Member  
 `InstructionOffset`  
 Der Anweisungszeiger.  
  
 `ReturnOffset`  
 Die Rückgabeadresse.  
  
 `FrameOffset`  
 Der Framezeiger.  
  
 `StackOffset`  
 Der Stapelzeiger.  
  
## Hinweise  
 Die `JS_NATIVE_FRAME`\-Struktur wird von `IJsStackFrameEnumerator` verwendet.  
  
## Siehe auch  
 [Konstanten, Enumerationen und Strukturen für Active Script\-Debugger](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)