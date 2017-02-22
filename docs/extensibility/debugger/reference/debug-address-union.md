---
title: "DEBUG_ADDRESS_UNION | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "DEBUG_ADDRESS_UNION"
helpviewer_keywords: 
  - "DEBUG_ADDRESS_UNION union"
ms.assetid: e3d11aab-de0d-4109-b5dc-11e07e64382d
caps.latest.revision: 9
caps.handback.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
---
# DEBUG_ADDRESS_UNION
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Beschreibt verschiedene Arten von Adressen.  
  
## Syntax  
  
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
  
```c#  
public struct DEBUG_ADDRESS_UNION {  
   public ADDRESS_KIND dwKind;  
   public IntPtr       unionmember;  
}  
```  
  
## Ausdrücke  
 dwKind  
 Ein Wert aus der [ADDRESS\_KIND](../../../extensibility/debugger/reference/address-kind.md)\-Enumeration, die angibt, wie die Gesamtmenge interpretiert.  
  
 addr.addrNative  
 \[C\+\+\] Es enthält die [NATIVE\_ADDRESS](../../../extensibility/debugger/reference/native-address.md) Struktur wenn `dwKind` \= ADDRESS\_KIND\_NATIVE.  
  
 addr.addrThisRel  
 \[C\+\+\] Es enthält die[UNMANAGED\_ADDRESS\_THIS\_RELATIVE](../../../extensibility/debugger/reference/unmanaged-address-this-relative.md) Struktur wenn `dwKind` \= ADDRESS\_KIND\_UNMANAGED\_THIS\_RELATIVE.  
  
 addr.addUPhysical  
 \[C\+\+\] Es enthält die[UNMANAGED\_ADDRESS\_PHYSICAL](../../../extensibility/debugger/reference/unmanaged-address-physical.md) Struktur wenn `dwKind` \= ADDRESS\_KIND\_UNMANAGED\_PHYSICAL.  
  
 addr.addrMethod  
 \[C\+\+\] Es enthält die[METADATA\_ADDRESS\_METHOD](../../../extensibility/debugger/reference/metadata-address-method.md) Struktur wenn `dwKind` \= ADDRESS\_KIND\_METHOD.  
  
 addr.addrField  
 \[C\+\+\] Es enthält die[METADATA\_ADDRESS\_FIELD](../../../extensibility/debugger/reference/metadata-address-field.md) Struktur wenn `dwKind` \= ADDRESS\_KIND\_FIELD.  
  
 addr.addrLocal  
 \[C\+\+\] Es enthält die[METADATA\_ADDRESS\_LOCAL](../../../extensibility/debugger/reference/metadata-address-local.md) Struktur wenn `dwKind` \= ADDRESS\_KIND\_LOCAL.  
  
 addr.addrParam  
 \[C\+\+\] Es enthält die[METADATA\_ADDRESS\_PARAM](../../../extensibility/debugger/reference/metadata-address-param.md) Struktur wenn `dwKind` \= ADDRESS\_KIND\_PARAM.  
  
 addr.addrArrayElem  
 \[C\+\+\] Es enthält die[METADATA\_ADDRESS\_ARRAYELEM](../../../extensibility/debugger/reference/metadata-address-arrayelem.md) Struktur wenn `dwKind` \= ADDRESS\_KIND\_ARRAYELEM.  
  
 addr.addrRetVal  
 \[C\+\+\] Es enthält die[METADATA\_ADDRESS\_RETVAL](../../../extensibility/debugger/reference/metadata-address-retval.md) Struktur wenn `dwKind` \= ADDRESS\_KIND\_RETVAL.  
  
 addr.unused  
 \[C\+\+\] Nur auffüllen.  
  
 Adr  
 \[C\+\+\] Es wird nur der Name der Union.  
  
 unionmember  
 \[Nur C\#\] muss dieser Wert in den entsprechenden Strukturtyp auf Grundlage `dwKind`gemarshallt werden.  Siehe Hinweise für die Zuordnung zwischen `dwKind` und Interpretation der Union.  
  
## Hinweise  
 Diese Struktur ist Teil der [DEBUG\_ADDRESS](../../../extensibility/debugger/reference/debug-address.md) Struktur und stellt eine von mehreren unterschiedlichen Arten von Adressen dar \(die `DEBUG_ADDRESS` Struktur wird von einem Aufruf der [GetAddress](../../../extensibility/debugger/reference/idebugaddress-getaddress.md)\-Methode gefüllt\).  
  
 \[C\#\] zeigt nur die folgende Tabelle veranschaulicht, wie der `unionmember`\-Member für jede Art Adresse interpretiert.  Im Beispiel wird gezeigt, wie dies für eine Weise Adresse.  
  
|`dwKind`|`unionmember` wie interpretierte|  
|--------------|--------------------------------------|  
|`ADDRESS_KIND_NATIVE`|[NATIVE\_ADDRESS](../../../extensibility/debugger/reference/native-address.md)|  
|`ADDRESS_KIND_UNMANAGED_THIS_RELATIVE`|[UNMANAGED\_ADDRESS\_THIS\_RELATIVE](../../../extensibility/debugger/reference/unmanaged-address-this-relative.md)|  
|`ADDRESS_KIND_UNMANAGED_PHYSICAL`|[UNMANAGED\_ADDRESS\_PHYSICAL](../../../extensibility/debugger/reference/unmanaged-address-physical.md)|  
|`ADDRESS_KIND_METHOD`|[METADATA\_ADDRESS\_METHOD](../../../extensibility/debugger/reference/metadata-address-method.md)|  
|`ADDRESS_KIND_FIELD`|[METADATA\_ADDRESS\_FIELD](../../../extensibility/debugger/reference/metadata-address-field.md)|  
|`ADDRESS_KIND_LOCAL`|[METADATA\_ADDRESS\_LOCAL](../../../extensibility/debugger/reference/metadata-address-local.md)|  
|`ADDRESS_KIND_PARAM`|[METADATA\_ADDRESS\_PARAM](../../../extensibility/debugger/reference/metadata-address-param.md)|  
|`ADDRESS_KIND_ARRAYELEM`|[METADATA\_ADDRESS\_ARRAYELEM](../../../extensibility/debugger/reference/metadata-address-arrayelem.md)|  
|`ADDRESS_KIND_RETVAL`|[METADATA\_ADDRESS\_RETVAL](../../../extensibility/debugger/reference/metadata-address-retval.md)|  
  
## Beispiel  
 Dieses Beispiel zeigt, wie eine Adresse \(`METADATA_ADDRESS_ARRAYELEM`\) der `DEBUG_ADDRESS_UNION` Struktur in C\# interpretiert.  Die übrigen Elemente können auf genau die gleiche Art interpretiert werden.  
  
```c#  
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
  
## Anforderungen  
 Header: sh.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Siehe auch  
 [Strukturen und Unions](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [DEBUG\_ADDRESS](../../../extensibility/debugger/reference/debug-address.md)   
 [ADDRESS\_KIND](../../../extensibility/debugger/reference/address-kind.md)   
 [GetAddress](../../../extensibility/debugger/reference/idebugaddress-getaddress.md)