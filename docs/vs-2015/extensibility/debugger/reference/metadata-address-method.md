---
title: METADATA_ADDRESS_METHOD | Microsoft-Dokumentation
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
- METADATA_ADDRESS_METHOD
helpviewer_keywords:
- METADATA_ADDRESS_METHOD structure
ms.assetid: fc0e5370-1b4f-4867-837f-0d63c4b9dd09
caps.latest.revision: 7
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: be74663ad9e210ec8211c71b2a20eb93c03e9287
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47511915"
---
# <a name="metadataaddressmethod"></a>METADATA_ADDRESS_METHOD
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [METADATA_ADDRESS_METHOD](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/metadata-address-method).  
  
Diese Struktur stellt die Adresse einer Methode einer Klasse dar.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
typedef struct _tagMETADATA_ADDRESS_METHOD {  
   _mdToken tokMethod;  
   DWORD    dwOffset;  
   DWORD    dwVersion;  
} METADATA_ADDRESS_METHOD;  
```  
  
```csharp  
public struct METADATA_ADDRESS_METHOD {  
   public int  tokMethod;  
   public uint dwOffset;  
   public uint dwVersion;  
}  
```  
  
## <a name="terms"></a>Begriffe  
 tokMethod  
 Die ID der Methode.  
  
 [C++] `_mdToken` ist eine `typedef` für eine 32-Bit- `int`.  
  
 dwOffset  
 Der Offset von der Klasse beginnen, diese Methode (kann den Offset in der Vtable darstellen).  
  
 dwVersion  
 Die Version der Methode (dieser Wert ist nur für die symbolanbieter).  
  
## <a name="remarks"></a>Hinweise  
 Diese Struktur ist Teil der Union in der [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md) Kontostruktur, wenn die `dwKind` Feld der `DEBUG_ADDRESS_UNION` Struktur nastaven NA hodnotu `ADDRESS_KIND_METHOD` (ein Wert aus der [ADDRESS_KIND](../../../extensibility/debugger/reference/address-kind.md) die Enumeration).  
  
## <a name="requirements"></a>Anforderungen  
 Header: sh.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Siehe auch  
 [Strukturen und Unions](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md)   
 [ADDRESS_KIND](../../../extensibility/debugger/reference/address-kind.md)

