---
title: DEBUG_ADDRESS_UNION | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: DEBUG_ADDRESS_UNION
helpviewer_keywords: DEBUG_ADDRESS_UNION union
ms.assetid: e3d11aab-de0d-4109-b5dc-11e07e64382d
caps.latest.revision: "9"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: e7f2f01ee30949fc5b82f2bba868e433a4f3a14e
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="debugaddressunion"></a>DEBUG_ADDRESS_UNION
Beschreibt die verschiedene Arten von Adressen.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
typedef struct _tagDEBUG_ADDRESS_UNION {  
   ADDRESS_KIND dwKind;  
   union {  
      NATIVE_ADDRESS                  addrNative;  
      UNMANAGED_ADDRESS_THIS_RELATIVE addrThisRel;  
      UNMANAGED_ADDRESS_PHYSICAL      addrUPhysical;  
      METADATA_ADDRESS_METHOD         addrMethod;  
      METADATA_ADDRESS_FIELD          addrField;  
      METADATA_ADDRESS_LOCAL          addrLocal;  
      METADATA_ADDRESS_PARAM          addrParam;  
      METADATA_ADDRESS_ARRAYELEM      addrArrayElem;  
      METADATA_ADDRESS_RETVAL         addrRetVal;  
      DWORD                           unused;  
   } addr;  
} DEBUG_ADDRESS_UNION;  
```  
  
```csharp  
public struct DEBUG_ADDRESS_UNION {  
   public ADDRESS_KIND dwKind;  
   public IntPtr       unionmember;  
}  
```  
  
## <a name="terms"></a>Begriffe  
 dwKind  
 Ein Wert aus der [ADDRESS_KIND](../../../extensibility/debugger/reference/address-kind.md) Enumeration, der angibt, wie die Union zu interpretieren.  
  
 addr.addrNative  
 [Nur C++] Enthält die [NATIVE_ADDRESS](../../../extensibility/debugger/reference/native-address.md) Struktur, wenn `dwKind` = ADDRESS_KIND_NATIVE.  
  
 addr.addrThisRel  
 [Nur C++] Enthält die[UNMANAGED_ADDRESS_THIS_RELATIVE](../../../extensibility/debugger/reference/unmanaged-address-this-relative.md) Struktur, wenn `dwKind` = ADDRESS_KIND_UNMANAGED_THIS_RELATIVE.  
  
 addr.addUPhysical  
 [Nur C++] Enthält die[UNMANAGED_ADDRESS_PHYSICAL](../../../extensibility/debugger/reference/unmanaged-address-physical.md) Struktur, wenn `dwKind` = ADDRESS_KIND_UNMANAGED_PHYSICAL.  
  
 addr.addrMethod  
 [Nur C++] Enthält die[METADATA_ADDRESS_METHOD](../../../extensibility/debugger/reference/metadata-address-method.md) Struktur, wenn `dwKind` = ADDRESS_KIND_METHOD.  
  
 addr.addrField  
 [Nur C++] Enthält die[METADATA_ADDRESS_FIELD](../../../extensibility/debugger/reference/metadata-address-field.md) Struktur, wenn `dwKind` = ADDRESS_KIND_FIELD.  
  
 addr.addrLocal  
 [Nur C++] Enthält die[METADATA_ADDRESS_LOCAL](../../../extensibility/debugger/reference/metadata-address-local.md) Struktur, wenn `dwKind` = ADDRESS_KIND_LOCAL.  
  
 addr.addrParam  
 [Nur C++] Enthält die[METADATA_ADDRESS_PARAM](../../../extensibility/debugger/reference/metadata-address-param.md) Struktur, wenn `dwKind` = ADDRESS_KIND_PARAM.  
  
 addr.addrArrayElem  
 [Nur C++] Enthält die[METADATA_ADDRESS_ARRAYELEM](../../../extensibility/debugger/reference/metadata-address-arrayelem.md) Struktur, wenn `dwKind` = ADDRESS_KIND_ARRAYELEM.  
  
 addr.addrRetVal  
 [Nur C++] Enthält die[METADATA_ADDRESS_RETVAL](../../../extensibility/debugger/reference/metadata-address-retval.md) Struktur, wenn `dwKind` = ADDRESS_KIND_RETVAL.  
  
 addr.Unused  
 [Nur C++-Code] Auffüllung.  
  
 addr  
 [Nur C++] Der Name der Union.  
  
 Unionmember  
 [C#] Dieser Wert muss auf den entsprechenden Strukturtyp basierend auf gemarshallt werden `dwKind`. Finden Sie unter "Hinweise" für die Zuordnung zwischen `dwKind` und Interpretation der Union.  
  
## <a name="remarks"></a>Hinweise  
 Diese Struktur ist Teil der [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md) Struktur und eines aus einer Reihe von verschiedenen Arten von Adressen darstellt (die `DEBUG_ADDRESS` Struktur wird ausgefüllt, durch einen Aufruf der [GetAddress](../../../extensibility/debugger/reference/idebugaddress-getaddress.md) Methode).  
  
 [C#] Die folgende Tabelle zeigt die Interpretation der `unionmember` Member für jede Art von Adresse. Im Beispiel wird gezeigt, wie dies für eine Art der Adresse erfolgt.  
  
|`dwKind`|`unionmember`interpretiert als|  
|--------------|----------------------------------|  
|`ADDRESS_KIND_NATIVE`|[NATIVE_ADDRESS](../../../extensibility/debugger/reference/native-address.md)|  
|`ADDRESS_KIND_UNMANAGED_THIS_RELATIVE`|[UNMANAGED_ADDRESS_THIS_RELATIVE](../../../extensibility/debugger/reference/unmanaged-address-this-relative.md)|  
|`ADDRESS_KIND_UNMANAGED_PHYSICAL`|[UNMANAGED_ADDRESS_PHYSICAL](../../../extensibility/debugger/reference/unmanaged-address-physical.md)|  
|`ADDRESS_KIND_METHOD`|[METADATA_ADDRESS_METHOD](../../../extensibility/debugger/reference/metadata-address-method.md)|  
|`ADDRESS_KIND_FIELD`|[METADATA_ADDRESS_FIELD](../../../extensibility/debugger/reference/metadata-address-field.md)|  
|`ADDRESS_KIND_LOCAL`|[METADATA_ADDRESS_LOCAL](../../../extensibility/debugger/reference/metadata-address-local.md)|  
|`ADDRESS_KIND_PARAM`|[METADATA_ADDRESS_PARAM](../../../extensibility/debugger/reference/metadata-address-param.md)|  
|`ADDRESS_KIND_ARRAYELEM`|[METADATA_ADDRESS_ARRAYELEM](../../../extensibility/debugger/reference/metadata-address-arrayelem.md)|  
|`ADDRESS_KIND_RETVAL`|[METADATA_ADDRESS_RETVAL](../../../extensibility/debugger/reference/metadata-address-retval.md)|  
  
## <a name="example"></a>Beispiel  
 In diesem Beispiel wird gezeigt, wie eine Art der Adresse interpretiert werden sollen (`METADATA_ADDRESS_ARRAYELEM`) von der `DEBUG_ADDRESS_UNION` Struktur in C# geschrieben. Die übrigen Elemente können auf genau die gleiche Weise interpretiert werden.  
  
```csharp  
using System;  
using System.Runtime.Interop.Services;  
using Microsoft.VisualStudio.Debugger.Interop;  
  
namespace MyPackage  
{  
    public class MyClass  
    {  
        public void Interpret(DEBUG_ADDRESS_UNION dau)  
        {  
            if (dau.dwKind == (uint)enum_ADDRESS_KIND.ADDRESS_KIND_METADATA_ARRAYELEM)  
            {  
                 METADATA_ADDRESS_ARRAYELEM arrayElem =  
                     (METADATA_ADDRESS_ARRAYELEM)Marshal.PtrToStructure(dau.unionmember,  
                                 typeof(METADATA_ADDRESS_ARRAYELEM));  
            }  
        }  
    }  
}  
```  
  
## <a name="requirements"></a>Anforderungen  
 Header: sh.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Siehe auch  
 [Strukturen und Unions](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md)   
 [ADDRESS_KIND](../../../extensibility/debugger/reference/address-kind.md)   
 [GetAddress](../../../extensibility/debugger/reference/idebugaddress-getaddress.md)