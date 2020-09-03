---
title: UNMANAGED_ADDRESS_PHYSICAL | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- UNMANAGED_ADDRESS_PHYSICAL
helpviewer_keywords:
- UNMANAGED_ADDRESS_PHYSICAL structure
ms.assetid: fed09686-caa6-4efc-851e-a0432019e9d0
caps.latest.revision: 7
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 8f8eccadbb2ae29f684c8c760ab34dae59c79ac7
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68204763"
---
# <a name="unmanaged_address_physical"></a>UNMANAGED_ADDRESS_PHYSICAL
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Diese Struktur stellt eine physische Adresse dar.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
typedef struct _tagUNMANAGED_ADDRESS_PHYSICAL {  
   ULONGLONG offset;  
} UNMANAGED_ADDRESS_PHYSICAL;  
```  
  
```csharp  
public struct UNMANAGED_ADDRESS_PHYSICAL {  
   public ulong offset;  
}  
```  
  
## <a name="terms"></a>Begriffe  
 offset  
 Ein 64-Bit-Offset in einem physischen Adressraum.  
  
## <a name="remarks"></a>Bemerkungen  
 Diese Struktur ist Teil der Union in der [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md) -Struktur, wenn das- `dwKind` Feld der- `DEBUG_ADDRESS_UNION` Struktur auf festgelegt ist `ADDRESS_KIND_UNMANAGED_PHYSICAL` (ein Wert aus der [ADDRESS_KIND](../../../extensibility/debugger/reference/address-kind.md) Enumeration).  
  
## <a name="requirements"></a>Anforderungen  
 Header: sh. h  
  
 Namespace: Microsoft. VisualStudio. Debugger. Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Weitere Informationen  
 [Strukturen und Unions](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md)
