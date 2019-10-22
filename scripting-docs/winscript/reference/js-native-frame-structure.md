---
title: JS_NATIVE_FRAME-Struktur | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- JS_NATIVE_FRAME
apilocation:
- jscript9diag.dll
ms.assetid: 5afa2ee1-b3e2-47cb-b304-84f96e6fbb14
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a0b624229a96cfc2a2d2044a926f45fa91a1c76c
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/18/2019
ms.locfileid: "72571763"
---
# <a name="js_native_frame-structure"></a>JS_NATIVE_FRAME-Struktur
Stellt einen Stapelrahmen dar.  
  
## <a name="syntax"></a>Syntax  
  
```cpp
typedef struct {  
    UINT64 InstructionOffset;    UINT64 ReturnOffset;    UINT64 FrameOffset;    UINT64 StackOffset;  
} JS_NATIVE_FRAME;  
```  
  
## <a name="members"></a>Member  
 `InstructionOffset`  
 Der Anweisungszeiger.  
  
 `ReturnOffset`  
 Die Rückgabeadresse.  
  
 `FrameOffset`  
 Der Framezeiger.  
  
 `StackOffset`  
 Der Stapelzeiger.  
  
## <a name="remarks"></a>Hinweise  
 Die `JS_NATIVE_FRAME`-Struktur wird von `IJsStackFrameEnumerator` verwendet.  
  
## <a name="see-also"></a>Siehe auch  
 [Konstanten, Enumerationen und Strukturen für Active Script-Debugger](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)