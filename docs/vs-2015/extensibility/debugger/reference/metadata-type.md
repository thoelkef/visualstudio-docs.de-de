---
title: METADATA_TYPE | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- METADATA_TYPE
helpviewer_keywords:
- METADATA_TYPE structure
ms.assetid: 2d8b78f6-0aef-4d79-809a-cff9b2c24659
caps.latest.revision: 8
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 1be7cb6071a0307a56285b8929e52e038c263fdc
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "62546823"
---
# <a name="metadata_type"></a>METADATA_TYPE
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Diese Struktur gibt Informationen zu einem Feldtyp an, der aus Metadaten entnommen wurde.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
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
 ulappdomainid  
 Die ID der Anwendung, von der das Symbol stammt. Hiermit wird eine Instanz der Anwendung eindeutig identifiziert.  
  
 guidmodule  
 Der GUID des Moduls, das dieses Feld enthält.  
  
 "dekclass"  
 Die Metadatentoken-ID dieses Typs.  
  
 [C++] `_mdToken` ist eine `typedef` für ein 32-Bit- `int` .  
  
## <a name="remarks"></a>Bemerkungen  
 Diese Struktur wird als Teil der Union in der [TYPE_INFO](../../../extensibility/debugger/reference/type-info.md) -Struktur angezeigt, wenn das- `dwKind` Feld der- `TYPE_INFO` Struktur auf festgelegt ist `TYPE_KIND_METADATA` (ein Wert aus der [dwTYPE_KIND](../../../extensibility/debugger/reference/dwtype-kind.md) Enumeration).  
  
 Der `tokClass` Wert ist ein Metadatentoken, das einen Typ eindeutig identifiziert. Ausführliche Informationen zum Interpretieren der oberen Bits der Metadatentoken-ID finden Sie in der- `CorTokenType` Enumeration in der Datei "corhdr. h" im [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] SDK.  
  
## <a name="requirements"></a>Anforderungen  
 Header: sh. h  
  
 Namespace: Microsoft. VisualStudio. Debugger. Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Weitere Informationen  
 [Strukturen und Unions](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [TYPE_INFO](../../../extensibility/debugger/reference/type-info.md)   
 [dwTYPE_KIND](../../../extensibility/debugger/reference/dwtype-kind.md)
