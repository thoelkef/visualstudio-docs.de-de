---
title: FIELD_INFO | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/15/2016
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
ms.openlocfilehash: 4512663c69ba652917b77ebe2a24cef374887c2e
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49940527"
---
# <a name="fieldinfo"></a>FIELD_INFO
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

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

