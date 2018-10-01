---
title: DEBUG_REFERENCE_INFO | Microsoft-Dokumentation
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
- DEBUG_REFERENCE_INFO
helpviewer_keywords:
- DEBUG_REFERENCE_INFO structure
ms.assetid: 24b83d00-d756-42a1-8083-730f998761dc
caps.latest.revision: 9
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 0fc0819e323e477fea8e2cc3ba2cddb6338c2861
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47522918"
---
# <a name="debugreferenceinfo"></a>DEBUG_REFERENCE_INFO
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [DEBUG_REFERENCE_INFO](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/debug-reference-info).  
  
Beschreibt einen Verweis an.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
typedef struct tagDEBUG_REFERENCE_INFO {   
   DEBUGREF_INFO_FLAGS dwFields;  
   BSTR                bstrName;  
   BSTR                bstrType;  
   BSTR                bstrValue;  
   DBG_ATTRIB_FLAGS    dwAttrib;  
   REFERENCE_TYPE.     dwRefType;  
   IDebugReference2*   m_pReference;  
} DEBUG_REFERENCE_INFO;  
```  
  
```csharp  
public struct DEBUG_REFERENCE_INFO {   
   public uint             dwFields;  
   public string           bstrName;  
   public string           bstrType;  
   public string           bstrValue;  
   public ulong            dwAttrib;  
   public uint.            dwRefType;  
   public IDebugReference2 m_pReference;  
};  
```  
  
## <a name="members"></a>Member  
 dwFields  
 Eine Kombination von Flags aus der [DEBUGREF_INFO_FLAGS](../../../extensibility/debugger/reference/debugref-info-flags.md) Enumeration, der angibt, welche Felder ausgefüllt sind.  
  
 bstrName  
 Die vom Benutzer angegebener Name des der [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md) Objekt.  
  
 bstrType  
 Der Verweistyp als formatierte Zeichenfolge.  
  
 bstrValue  
 Der Verweiswert als formatierte Zeichenfolge  
  
 dwAttrib  
 Eine Kombination von Flags aus der [DBG_ATTRIB_FLAGS](../../../extensibility/debugger/reference/dbg-attrib-flags.md) Enumeration, die die Flags für die Attribute der Debug-Eigenschaft angibt.  
  
 dwRefType  
 Ein Wert aus der [REFERENCE_TYPE](../../../extensibility/debugger/reference/reference-type.md) -Enumeration, der angibt, ob der Verweistyp stark oder schwach ist.  
  
 m_pReference  
 Ein [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md) Objekt, das die Verweisinformationen angibt.  
  
## <a name="remarks"></a>Hinweise  
 Diese Struktur wird auf den Aufruf zum Übergeben der [GetReferenceInfo](../../../extensibility/debugger/reference/idebugreference2-getreferenceinfo.md) Methode gefüllt werden soll. Diese Struktur wird auch zurückgegeben, als Teil einer Liste von der [IEnumDebugReferenceInfo2](../../../extensibility/debugger/reference/ienumdebugreferenceinfo2.md) -Schnittstelle, die wiederum von einem Aufruf zurückgegeben wird das [EnumChildren](../../../extensibility/debugger/reference/idebugreference2-enumchildren.md) Methode.  
  
## <a name="requirements"></a>Anforderungen  
 Header: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Siehe auch  
 [Strukturen und Unions](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)   
 [DEBUGREF_INFO_FLAGS](../../../extensibility/debugger/reference/debugref-info-flags.md)   
 [DBG_ATTRIB_FLAGS](../../../extensibility/debugger/reference/dbg-attrib-flags.md)   
 [REFERENCE_TYPE](../../../extensibility/debugger/reference/reference-type.md)   
 [GetReferenceInfo](../../../extensibility/debugger/reference/idebugreference2-getreferenceinfo.md)   
 [EnumChildren](../../../extensibility/debugger/reference/idebugreference2-enumchildren.md)   
 [IEnumDebugReferenceInfo2](../../../extensibility/debugger/reference/ienumdebugreferenceinfo2.md)

