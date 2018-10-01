---
title: BP_RES_DATA_FLAGS | Microsoft-Dokumentation
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
- BP_RES_DATA_FLAGS
helpviewer_keywords:
- BP_RES_DATA_FLAGS enumeration
ms.assetid: d97611e2-def6-45a9-ad7d-eedf2ad4c82b
caps.latest.revision: 9
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: f5377478021c9c69a7a7e912163c091849df796c
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47515984"
---
# <a name="bpresdataflags"></a>BP_RES_DATA_FLAGS
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [BP_RES_DATA_FLAGS](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/bp-res-data-flags).  
  
Gibt an, ob der Datenhaltepunkt emuliert wird oder in implementiert Hardware.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
enum enum_BP_RES_DATA_FLAGS {   
   BP_RES_DATA_EMULATED = 0x0001  
};  
typedef DWORD BP_RES_DATA_FLAGS;  
```  
  
```csharp  
public enum enum_BP_RES_DATA_FLAGS {   
   BP_RES_DATA_EMULATED = 0x0001  
};  
```  
  
## <a name="members"></a>Member  
 BP_RES_DATA_EMULATED  
 Gibt an, dass es sich bei der Datenhaltepunkt emuliert wird.  
  
## <a name="remarks"></a>Hinweise  
 Verwendet für die `dwFlags` Mitglied der [BP_RESOLUTION_DATA](../../../extensibility/debugger/reference/bp-resolution-data.md) Struktur.  
  
## <a name="requirements"></a>Anforderungen  
 Header: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Siehe auch  
 [Enumerationen](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [BP_RESOLUTION_DATA](../../../extensibility/debugger/reference/bp-resolution-data.md)

