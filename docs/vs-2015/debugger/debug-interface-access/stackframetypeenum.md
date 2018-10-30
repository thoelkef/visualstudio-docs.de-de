---
title: StackFrameTypeEnum | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- StackFrameTypeEnum enumeration
ms.assetid: 61e40163-eee0-4c1f-af47-cef3771bdc41
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 32f4f4082c68b455baeb00c8e0364999b606473c
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49950172"
---
# <a name="stackframetypeenum"></a>StackFrameTypeEnum
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Gibt den Stack-Frame-Typ.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
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
 Standard EBP-Stapelrahmen.  
  
 `FrameTypeFrameData`  
 Frame-Pointer ausgelassen; Frame-Daten-Informationen verfügbar.  
  
 `FrameTypeUnknown`  
 Frame aus, der kein Debuginformationen vorhanden wären.  
  
## <a name="remarks"></a>Hinweise  
 Die Werte in dieser Enumeration werden zurückgegeben, durch einen Aufruf der [idiastackframe:: Get_type](../../debugger/debug-interface-access/idiastackframe-get-type.md) Methode.  
  
## <a name="requirements"></a>Anforderungen  
 Header: cvconst.h  
  
## <a name="see-also"></a>Siehe auch  
 [Enumerationen und Strukturen](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [IDiaStackFrame::get_type](../../debugger/debug-interface-access/idiastackframe-get-type.md)



