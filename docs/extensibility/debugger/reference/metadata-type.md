---
title: METADATA_TYPE | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- METADATA_TYPE
helpviewer_keywords:
- METADATA_TYPE structure
ms.assetid: 2d8b78f6-0aef-4d79-809a-cff9b2c24659
caps.latest.revision: 7
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
ms.openlocfilehash: f2fd53d0e6a0b92a3c8c7b030d503578aa9d2f98
ms.contentlocale: de-de
ms.lasthandoff: 09/26/2017

---
# <a name="metadatatype"></a>METADATA_TYPE
Diese Struktur gibt Informationen zu Metadaten entnommen Feldtyp an.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
typedef struct _tagTYPE_METADATA {  
   ULONG32  ulAppDomainID;  
   GUID     guidModule;  
   _mdToken tokClass;  
} METADATA_TYPE;  
```  
  
```csharp  
public struct METADATA_TYPE {  
   public uint ulAppDomainID;  
   public Guid guidModule;  
   public int  tokClass;  
};  
```  
  
#### <a name="parameters"></a>Parameter  
 ulAppDomainID  
 Die ID der Anwendung, von der das Symbol stammt. Dient zur eindeutigen Identifizierung eine Instanz der Anwendung.  
  
 guidModule  
 Die GUID des Moduls, das dieses Feld enthält.  
  
 tokClass  
 Die Metadaten token-ID dieses Typs.  
  
 [C++] `_mdToken` ist ein `typedef` für 32-Bit- `int`.  
  
## <a name="remarks"></a>Hinweise  
 Diese Struktur wird als Teil der Union der [TYPE_INFO](../../../extensibility/debugger/reference/type-info.md) strukturieren, wenn die `dwKind` -Feld der der `TYPE_INFO` Struktur auf festgelegt ist `TYPE_KIND_METADATA` (ein Wert aus der [DwTYPE_KIND](../../../extensibility/debugger/reference/dwtype-kind.md) die Enumeration).  
  
 Die `tokClass` Wert ist ein Metadatentoken, das einen Typ eindeutig identifiziert. Weitere Informationen zum Interpretieren der höherwertigen Bits der Metadaten-token-ID finden Sie unter der `CorTokenType` Aufzählung der in der Datei "corhdr.h" in der [!INCLUDE[dnprdnshort](../../../code-quality/includes/dnprdnshort_md.md)] SDK.  
  
## <a name="requirements"></a>Anforderungen  
 Header: sh.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Siehe auch  
 [Strukturen und Unions](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [TYPE_INFO](../../../extensibility/debugger/reference/type-info.md)   
 [dwTYPE_KIND](../../../extensibility/debugger/reference/dwtype-kind.md)
