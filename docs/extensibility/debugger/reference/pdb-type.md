---
title: PDB_TYPE | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- PDB_TYPE
helpviewer_keywords:
- PDB_TYPE structure
ms.assetid: 1c1bb772-77d6-4870-90b2-fd9247d0004e
caps.latest.revision: 7
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: f1c08df8cf56d81ebb22fbdf17f3d20084599b51
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="pdbtype"></a>PDB_TYPE
Diese Struktur gibt Informationen über ein Symbol PDB entnommen Feldtyp an.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
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
 ulAppDomainID  
 Die ID der Anwendung, von der das Symbol stammt. Dient zur eindeutigen Identifizierung eine Instanz der Anwendung.  
  
 guidModule  
 Die GUID des Moduls, das dieses Feld enthält.  
  
 symid  
 Die ID des Symbols, das dieses Feld entspricht.  
  
## <a name="remarks"></a>Hinweise  
 Diese Struktur wird als Teil der Union der [TYPE_INFO](../../../extensibility/debugger/reference/type-info.md) strukturieren, wenn die `dwKind` -Feld der der `TYPE_INFO` Struktur auf festgelegt ist `TYPE_KIND_PDB` (ein Wert aus der [DwTYPE_KIND](../../../extensibility/debugger/reference/dwtype-kind.md) die Enumeration).  
  
## <a name="requirements"></a>Anforderungen  
 Header: sh.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Siehe auch  
 [Strukturen und Unions](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [TYPE_INFO](../../../extensibility/debugger/reference/type-info.md)   
 [dwTYPE_KIND](../../../extensibility/debugger/reference/dwtype-kind.md)