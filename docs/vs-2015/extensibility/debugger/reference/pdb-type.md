---
title: PDB_TYPE | Microsoft-Dokumentation
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
- PDB_TYPE
helpviewer_keywords:
- PDB_TYPE structure
ms.assetid: 1c1bb772-77d6-4870-90b2-fd9247d0004e
caps.latest.revision: 8
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 1e63fb8f32e6d28428a8b3f52196f37bdca0da81
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47514969"
---
# <a name="pdbtype"></a>PDB_TYPE
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [PDB_TYPE](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/pdb-type).  
  
Diese Struktur gibt Informationen über einen Feldtyp, ein Symbol für die PDB-Datei entnommen.  
  
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
 ulAppDomainID  
 Die ID der Anwendung, von der das Symbol stammt. Dies wird verwendet, um eine Instanz der Anwendung eindeutig zu identifizieren.  
  
 guidModule  
 Die GUID des Moduls, das dieses Feld enthält.  
  
 symid  
 Die ID des Symbols, das dieses Feld entspricht.  
  
## <a name="remarks"></a>Hinweise  
 Diese Struktur wird als Teil der Union in der [TYPE_INFO](../../../extensibility/debugger/reference/type-info.md) Kontostruktur, wenn die `dwKind` Feld der `TYPE_INFO` Struktur nastaven NA hodnotu `TYPE_KIND_PDB` (ein Wert aus der [DwTYPE_KIND](../../../extensibility/debugger/reference/dwtype-kind.md) die Enumeration).  
  
## <a name="requirements"></a>Anforderungen  
 Header: sh.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Siehe auch  
 [Strukturen und Unions](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [TYPE_INFO](../../../extensibility/debugger/reference/type-info.md)   
 [dwTYPE_KIND](../../../extensibility/debugger/reference/dwtype-kind.md)

