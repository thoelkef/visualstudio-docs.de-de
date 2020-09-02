---
title: METADATA_ADDRESS_ARRAYELEM | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- METADATA_ADDRESS_ARRAYELEM
helpviewer_keywords:
- METADATA_ADDRESS_ARRAYELEM structure
ms.assetid: 24321be5-7c17-4038-82a1-c20a2b68ff3c
caps.latest.revision: 7
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: f558dc11f4f338cd370442bf9feaed419ce29411
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "62547584"
---
# <a name="metadata_address_arrayelem"></a>METADATA_ADDRESS_ARRAYELEM
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Diese Struktur stellt ein Array Element innerhalb eines Arrays dar.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
typedef struct _tagMETADATA_ADDRESS_ARRAYELEM {  
   _mdToken tokMethod;  
   DWORD    dwIndex;  
} METADATA_ADDRESS_ARRAYELEM;  
```  
  
```csharp  
public struct METADATA_ADDRESS_ARRAYELEM {  
   public int  tokMethod;  
   public uint dwIndex;  
}  
```  
  
## <a name="terms"></a>Begriffe  
 "dekmethod"  
 Die ID des Arrays, zu dem dieses Element gehört.  
  
 [C++] `_mdToken` ist eine `typedef` für ein 32-Bit- `int` .  
  
 dwIndex  
 Der Index dieses Elements innerhalb des Arrays.  
  
## <a name="remarks"></a>Bemerkungen  
 Diese Struktur ist Teil der Union in der [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md) -Struktur, wenn das- `dwKind` Feld der- `DEBUG_ADDRESS_UNION` Struktur auf festgelegt ist `ADDRESS_KIND_ARRAYELEM` (ein Wert aus der [ADDRESS_KIND](../../../extensibility/debugger/reference/address-kind.md) Enumeration).  
  
## <a name="requirements"></a>Anforderungen  
 Header: sh. h  
  
 Namespace: Microsoft. VisualStudio. Debugger. Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Weitere Informationen  
 [Strukturen und Unions](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md)   
 [ADDRESS_KIND](../../../extensibility/debugger/reference/address-kind.md)
