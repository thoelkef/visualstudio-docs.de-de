---
title: FIELD_INFO | Microsoft-Dokumentation
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
- FIELD_INFO
helpviewer_keywords:
- FIELD_INFO structure
ms.assetid: bfafef6d-0c83-43d7-a779-1f0d24b166a1
caps.latest.revision: 15
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 1e0df86a61e490ec98759b2c66458a781f6cbaf1
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47514398"
---
# <a name="fieldinfo"></a>FIELD_INFO
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [FIELD_INFO](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/field-info).  
  
Diese Struktur wird eine lokale Variable, Parameter oder andere Feld beschrieben.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
typedef struct _tagFieldInfo {   
   FIELD_INFO_FIELDS dwFields;  
   BSTR              bstrFullName;  
   BSTR              bstrName;  
   BSTR              bstrType;  
   FIELD_MODIFIERS   dwModifiers;  
} FIELD_INFO;  
```  
  
```csharp  
public struct FIELD_INFO {  
   public uint   dwFields;  
   public string bstrFullName;  
   public string bstrName;  
   public string bstrType;  
   public uint   dwModifiers;  
};  
```  
  
## <a name="members"></a>Member  
 dwFields  
 Eine Kombination von Flags aus der [FIELD_INFO_FIELDS](../../../extensibility/debugger/reference/field-info-fields.md) Enumeration, der angibt, welche Elemente ausgefüllt werden.  
  
 bstrFullName  
 Der vollständige Name des Felds.  
  
 bstrName  
 Der kurze Name des Felds.  
  
 bstrType  
 Der Typ des Felds.  
  
 dwModifiers  
 Eine Kombination von Flags aus der [FIELD_MODIFIERS](../../../extensibility/debugger/reference/field-modifiers.md) -Enumeration, die das Feld beschreibt.  
  
## <a name="remarks"></a>Hinweise  
 Diese Struktur wird zum Übergeben der [GetInfo](../../../extensibility/debugger/reference/idebugfield-getinfo.md) Methode, in denen es ausgefüllt wird.  
  
## <a name="requirements"></a>Anforderungen  
 Header: sh.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Siehe auch  
 [Strukturen und Unions](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [FIELD_INFO_FIELDS](../../../extensibility/debugger/reference/field-info-fields.md)   
 [FIELD_MODIFIERS](../../../extensibility/debugger/reference/field-modifiers.md)   
 [GetInfo](../../../extensibility/debugger/reference/idebugfield-getinfo.md)

