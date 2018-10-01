---
title: STEPUNIT | Microsoft-Dokumentation
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- STEPUNIT
helpviewer_keywords:
- STEPUNIT enumeration
ms.assetid: cb8441f2-f744-4e73-acfe-ae8542df9649
caps.latest.revision: 9
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: adb9324cbc7a87e79a91d17d4a39f5a23c9679a6
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47516002"
---
# <a name="stepunit"></a>STEPUNIT
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [STEPUNIT](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/stepunit).  
  
Gibt die Schrittweite für die schrittweise Ausführung.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
enum enum_STEPUNIT {   
   STEP_STATEMENT   = 0,  
   STEP_LINE        = 1,  
   STEP_INSTRUCTION = 2  
};  
typedef DWORD STEPUNIT;  
```  
  
```csharp  
enum enum_STEPUNIT {   
   STEP_STATEMENT   = 0,  
   STEP_LINE        = 1,  
   STEP_INSTRUCTION = 2  
};  
```  
  
## <a name="members"></a>Member  
 STEP_STATEMENT  
 Schritte nach Anweisung.  
  
 STEP_LINE  
 Schritte nach Zeile.  
  
 STEP_INSTRUCTION  
 Schritte nach Anweisung.  
  
## <a name="remarks"></a>Hinweise  
 Übergeben als Argument an die [Schritt](../../../extensibility/debugger/reference/idebugprocess3-step.md) Methode.  
  
## <a name="requirements"></a>Anforderungen  
 Header: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Siehe auch  
 [Enumerationen](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [Step](../../../extensibility/debugger/reference/idebugprocess3-step.md)

