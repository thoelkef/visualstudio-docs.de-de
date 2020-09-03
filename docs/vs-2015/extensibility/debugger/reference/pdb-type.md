---
title: PDB_TYPE | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- PDB_TYPE
helpviewer_keywords:
- PDB_TYPE structure
ms.assetid: 1c1bb772-77d6-4870-90b2-fd9247d0004e
caps.latest.revision: 8
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: ad4b6a06a2a145daa85d780f4d23dfac9bebf7a0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68205111"
---
# <a name="pdb_type"></a>PDB_TYPE
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Diese Struktur gibt Informationen zu einem Feldtyp an, der aus einem PDB-Symbol entnommen wurde.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
typedef struct _tagTYPE_PDB {  
   ULONG32 ulAppDomainID;  
   GUID    guidModule;  
   DWORD   symid;  
} PDB_TYPE;  
```  
  
```csharp  
public struct PDB_TYPE {  
   public uint ulAppDomainID;  
   public Guid guidModule;  
   public uint symid;  
};  
```  
  
#### <a name="parameters"></a>Parameter  
 ulappdomainid  
 Die ID der Anwendung, von der das Symbol stammt. Hiermit wird eine Instanz der Anwendung eindeutig identifiziert.  
  
 guidmodule  
 Der GUID des Moduls, das dieses Feld enthält.  
  
 symid  
 Die ID des Symbols, das diesem Feld entspricht.  
  
## <a name="remarks"></a>Bemerkungen  
 Diese Struktur wird als Teil der Union in der [TYPE_INFO](../../../extensibility/debugger/reference/type-info.md) -Struktur angezeigt, wenn das- `dwKind` Feld der- `TYPE_INFO` Struktur auf festgelegt ist `TYPE_KIND_PDB` (ein Wert aus der [dwTYPE_KIND](../../../extensibility/debugger/reference/dwtype-kind.md) Enumeration).  
  
## <a name="requirements"></a>Anforderungen  
 Header: sh. h  
  
 Namespace: Microsoft. VisualStudio. Debugger. Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Weitere Informationen  
 [Strukturen und Unions](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [TYPE_INFO](../../../extensibility/debugger/reference/type-info.md)   
 [dwTYPE_KIND](../../../extensibility/debugger/reference/dwtype-kind.md)
