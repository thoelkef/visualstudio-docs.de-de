---
title: PROGRAM_DESTROY_FLAGS | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- PROGRAM_DESTROY_FLAGS enumeration
ms.assetid: be00d4a3-d5b8-4159-b632-64577f534883
caps.latest.revision: 8
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 9a9303eb738afc3ada918893e395b6a337a93bff
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49830482"
---
# <a name="programdestroyflags"></a>PROGRAM_DESTROY_FLAGS
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Listet die gültigen Werte des Programms zerstört Flags.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
enum enum_PPROGRAM_DESTROY_FLAGS  
{  
   PROGRAM_DESTROY_CONTINUE_DEBUGGING = 0x1  
};  
typedef DWORD PROGRAM_DESTROY_FLAGS;  
```  
  
```csharp  
public enum enum_PPROGRAM_DESTROY_FLAGS  
{  
   PROGRAM_DESTROY_CONTINUE_DEBUGGING = 0x1  
};  
```  
  
## <a name="terms"></a>Begriffe  
 PROGRAM_DESTROY_CONTINUE_DEBUGGING  
 Programm löschen, jedoch mit dem Debuggen fortfahren.  
  
## <a name="remarks"></a>Hinweise  
 Die Enumeration zurückgegeben wird, durch die [GetFlags](../../../extensibility/debugger/reference/idebugprogramdestroyeventflags2-getflags.md) Methode.  
  
## <a name="requirements"></a>Anforderungen  
 Header: Msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Siehe auch  
 [Enumerationen](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [GetFlags](../../../extensibility/debugger/reference/idebugprogramdestroyeventflags2-getflags.md)

