---
title: METADATA_TYPE | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- METADATA_TYPE
helpviewer_keywords:
- METADATA_TYPE structure
ms.assetid: 2d8b78f6-0aef-4d79-809a-cff9b2c24659
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8c276c34b902358ab355f1a67ffa1d97f4f0f8ce
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/25/2019
ms.locfileid: "55034713"
---
# <a name="metadatatype"></a>METADATA_TYPE
Diese Struktur gibt Informationen über einen Feldtyp aus Metadaten erstellt.  
  
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
 Die ID der Anwendung, von der das Symbol stammt. Dies wird verwendet, um eine Instanz der Anwendung eindeutig zu identifizieren.  
  
 guidModule  
 Die GUID des Moduls, das dieses Feld enthält.  
  
 tokClass  
 Die Metadaten token-ID dieses Typs.  
  
 [C++] `_mdToken` ist eine `typedef` für eine 32-Bit- `int`.  
  
## <a name="remarks"></a>Hinweise  
 Diese Struktur wird als Teil der Union in der [TYPE_INFO](../../../extensibility/debugger/reference/type-info.md) Kontostruktur, wenn die `dwKind` Feld der `TYPE_INFO` Struktur nastaven NA hodnotu `TYPE_KIND_METADATA` (ein Wert aus der [DwTYPE_KIND](../../../extensibility/debugger/reference/dwtype-kind.md) die Enumeration).  
  
 Die `tokClass` Wert ist ein Metadatentoken, das einen Typ eindeutig identifiziert. Weitere Informationen zum Interpretieren der höherwertigen Bits, der die Metadaten-token-ID finden Sie unter den `CorTokenType` Enumeration in der Datei "corhdr.h" in der [!INCLUDE[dnprdnshort](../../../code-quality/includes/dnprdnshort_md.md)] SDK.  
  
## <a name="requirements"></a>Anforderungen  
 Header: sh.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Siehe auch  
 [Strukturen und Unions](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [TYPE_INFO](../../../extensibility/debugger/reference/type-info.md)   
 [dwTYPE_KIND](../../../extensibility/debugger/reference/dwtype-kind.md)