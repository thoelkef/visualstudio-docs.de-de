---
title: StackFrameTypeEnum | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- StackFrameTypeEnum enumeration
ms.assetid: 61e40163-eee0-4c1f-af47-cef3771bdc41
caps.latest.revision: 10
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 655911bac1efbafe1838e24e2056282f9036479b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68179187"
---
# <a name="stackframetypeenum"></a>StackFrameTypeEnum
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Gibt den Stapel Rahmentyp an.  
  
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
  
## <a name="elements"></a>Elemente  
 `FrameTypeFPO`  
 Der Frame Zeiger wurde ausgelassen. Die verfügbaren Informationen zur Verfügbarkeit  
  
 `FrameTypeTrap`  
 Kerneltrap-Frame.  
  
 `FrameTypeTSS`  
 Kerneltrap-Frame.  
  
 `FrameTypeStandard`  
 Standard mäßiger EBP-Stapel Rahmen.  
  
 `FrameTypeFrameData`  
 Der Frame Zeiger wurde ausgelassen. Informationen zur Frame-Daten sind verfügbar.  
  
 `FrameTypeUnknown`  
 Frame, der keine Debuginformationen enthält.  
  
## <a name="remarks"></a>Bemerkungen  
 Die Werte in dieser Enumeration werden von einem Rückruf der [IDiaStackFrame:: get_type](../../debugger/debug-interface-access/idiastackframe-get-type.md) -Methode zurückgegeben.  
  
## <a name="requirements"></a>Anforderungen  
 Header: cvconst.h  
  
## <a name="see-also"></a>Weitere Informationen  
 [Enumerationen und Strukturen](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [IDiaStackFrame::get_type](../../debugger/debug-interface-access/idiastackframe-get-type.md)
