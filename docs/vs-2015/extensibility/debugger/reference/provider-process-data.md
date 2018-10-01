---
title: PROVIDER_PROCESS_DATA | Microsoft-Dokumentation
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
- PROVIDER_PROCESS_DATA
helpviewer_keywords:
- PROVIDER_PROCESS_DATA structure
ms.assetid: ec2362ed-4a0c-4a09-9d66-8ff04e4f41ee
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: fcc79cf8925b43cbd564170f6664fbf2b5dd327d
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47513950"
---
# <a name="providerprocessdata"></a>PROVIDER_PROCESS_DATA
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [PROVIDER_PROCESS_DATA](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/provider-process-data).  
  
Diese Struktur bietet Informationen zu Prozessen, die auf einem Computer ausgeführt wird.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
typedef struct tagPROVIDER_PROCESS_DATA {  
   PROVIDER_FIELDS    Fields;  
   PROGRAM_NODE_ARRAY ProgramNodes;  
   BOOL               fIsDebuggerPresent;  
} PROVIDER_PROCESS_DATA;  
```  
  
```csharp  
public struct PROVIDER_PROCESS_DATA {  
   public uint               Fields;  
   public PROGRAM_NODE_ARRAY ProgramNodes;  
   public int                fIsDebuggerPresent;  
}  
```  
  
## <a name="members"></a>Member  
 Felder  
 Eine Kombination von Flags aus der [PROVIDER_FIELDS](../../../extensibility/debugger/reference/provider-fields.md) Enumeration, der angibt, welche Felder ausgefüllt werden.  
  
 ProgramNodes  
 Ein [PROGRAM_NODE_ARRAY](../../../extensibility/debugger/reference/program-node-array.md) -Struktur, die ein Array von programmknoten enthält.  
  
 fIsDebuggerPresent  
 Ungleich Null (`TRUE`) Wenn die [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] Debugger ausgeführt wird, wird 0 (null) (`FALSE`) ist dies nicht.  
  
## <a name="remarks"></a>Hinweise  
 Diese Struktur wird zum Übergeben der [GetProviderProcessData](../../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprocessdata.md) Methode, in denen es ausgefüllt wird.  
  
## <a name="requirements"></a>Anforderungen  
 Header: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Siehe auch  
 [Strukturen und Unions](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [PROVIDER_FIELDS](../../../extensibility/debugger/reference/provider-fields.md)   
 [PROGRAM_NODE_ARRAY](../../../extensibility/debugger/reference/program-node-array.md)   
 [GetProviderProcessData](../../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprocessdata.md)

