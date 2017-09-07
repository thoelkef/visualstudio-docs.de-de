---
title: BP_RESOLUTION_DATA | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- BP_RESOLUTION_DATA
helpviewer_keywords:
- BP_RESOLUTION_DATA structure
ms.assetid: 9e0b9000-6a84-47b9-b07a-367a75764389
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: MT
ms.sourcegitcommit: 4a36302d80f4bc397128e3838c9abf858a0b5fe8
ms.openlocfilehash: f5be75214e9ab112cc3af17bd8bdcfae00083661
ms.contentlocale: de-de
ms.lasthandoff: 09/06/2017

---
# <a name="bpresolutiondata"></a>BP_RESOLUTION_DATA
Beschreibt das Ergebnis der Bindung eines Haltepunkts an.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
typedef struct _BP_RESOLUTION_DATA {   
   BSTR              bstrDataExpr;  
   BSTR              bstrFunc;  
   BSTR              bstrImage;  
   BP_RES_DATA_FLAGS dwFlags;  
} BP_RESOLUTION_DATA;  
```  
  
```csharp  
public struct BP_RESOLUTION_DATA {   
   public string bstrDataExpr;  
   public string bstrFunc;  
   public string bstrImage;  
   public uint   dwFlags;  
};  
```  
  
## <a name="members"></a>Member  
 `bstrDataExpr`  
 Die Datenausdruck, der gebunden wurde.  
  
 `bstrFunc`  
 Der Name der Funktion hat den Datenhaltepunkt bei (sofern vorhanden) gebunden.  
  
 `bstrImage`  
 Der Name des Moduls (z. B. MyModule.dll), die in den Datenhaltepunkt gebunden wurde.  
  
 `dwFlags`  
 Ein Wert aus der [BP_RES_DATA_FLAGS](../../../extensibility/debugger/reference/bp-res-data-flags.md) Enumeration, die beschreiben, wie den Datenhaltepunkt implementiert wird.  
  
## <a name="remarks"></a>Hinweise  
 Diese Struktur ist ein Mitglied der [BP_RESOLUTION_LOCATION](../../../extensibility/debugger/reference/bp-resolution-location.md) -Struktur, die aktivieren in ein Mitglied der [BP_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md) zurückgegebene Struktur der [GetResolutionInfo](../../../extensibility/debugger/reference/idebugbreakpointresolution2-getresolutioninfo.md)Methode.  
  
## <a name="requirements"></a>Anforderungen  
 Header: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Siehe auch  
 [Strukturen und Unions](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [BP_RESOLUTION_LOCATION](../../../extensibility/debugger/reference/bp-resolution-location.md)   
 [BP_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md)   
 [GetResolutionInfo](../../../extensibility/debugger/reference/idebugbreakpointresolution2-getresolutioninfo.md)
