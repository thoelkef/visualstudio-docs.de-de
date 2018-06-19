---
title: StackFrameTypeEnum | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- StackFrameTypeEnum enumeration
ms.assetid: 61e40163-eee0-4c1f-af47-cef3771bdc41
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 329661e857859a1f6452506ba2984ac962bf4ff2
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/18/2018
ms.locfileid: "31470815"
---
# <a name="stackframetypeenum"></a>StackFrameTypeEnum
Gibt den Stack-Frame-Typ.  
  
## <a name="syntax"></a>Syntax  
  
```C++  
enum StackFrameTypeEnum {  
   FrameTypeFPO,  
   FrameTypeTrap,  
   FrameTypeTSS,  
   FrameTypeStandard,  
   FrameTypeFrameData,  
   FrameTypeUnknown = -1  
};  
```  
  
## <a name="elements"></a>Elements  
 `FrameTypeFPO`  
 Frame-Pointer ausgelassen; FPO-Informationen verfügbar.  
  
 `FrameTypeTrap`  
 Kernel-Trap-Frame.  
  
 `FrameTypeTSS`  
 Kernel-Trap-Frame.  
  
 `FrameTypeStandard`  
 Standard EBP Stapelrahmen entspricht.  
  
 `FrameTypeFrameData`  
 Frame-Pointer ausgelassen; Frame Daten Informationen verfügbar.  
  
 `FrameTypeUnknown`  
 Rahmen, die über kein Debuginformationen vorhanden wären.  
  
## <a name="remarks"></a>Hinweise  
 Die Werte in dieser Enumeration werden zurückgegeben, durch einen Aufruf der [idiastackframe:: Get_type](../../debugger/debug-interface-access/idiastackframe-get-type.md) Methode.  
  
## <a name="requirements"></a>Anforderungen  
 Header: cvconst.h  
  
## <a name="see-also"></a>Siehe auch  
 [Enumerationen und Strukturen](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [IDiaStackFrame::get_type](../../debugger/debug-interface-access/idiastackframe-get-type.md)