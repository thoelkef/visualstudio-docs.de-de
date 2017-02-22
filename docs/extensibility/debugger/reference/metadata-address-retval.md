---
title: "METADATA_ADDRESS_RETVAL | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "METADATA_ADDRESS_RETVAL"
helpviewer_keywords: 
  - "METADATA_ADDRESS_RETVAL-Struktur"
ms.assetid: 5b0ec0fb-84b3-4ce7-8e24-becf3d881d7d
caps.latest.revision: 6
caps.handback.revision: 6
ms.author: "gregvanl"
manager: "ghogen"
---
# METADATA_ADDRESS_RETVAL
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Diese Struktur stellt einen Rückgabewert von einer Methode oder Funktion dar.  
  
## Syntax  
  
```cpp  
typedef struct _tagMETADATA_ADDRESS_RETVAL {  
   _mdToken tokMethod;  
   DWORD    dwCorType;  
   DWORD    dwSigSize;  
   BYTE     rgSig[10];  
} METADATA_ADDRESS_RETVAL;  
```  
  
```c#  
public struct METADATA_ADDRESS_RETVAL {  
   public int    tokMethod;  
   public uint   dwCorType;  
   public uint   dwSigSize;  
   public byte[] rgSig;  
}  
```  
  
## Begriffe  
 tokMethod  
 Die ID der Methode dieser Rückgabewert ist.  
  
 dwCorType  
 Der Basistyp des Rückgabewerts. Dies ist ein Wert aus der `CorElementType` \-Enumeration definiert, die der [!INCLUDE[dnprdnshort](../../../code-quality/includes/dnprdnshort_md.md)] SDK corhdr.h\-Datei.  
  
 dwSigSize  
 Die Größe der Signatur Rückgabewert \(gespeichert in `rgSig`\).  
  
 rgSig  
 Ein Array von Bytes, die die Signatur des Rückgabewerts bilden.  
  
## Hinweise  
 Diese Struktur ist Teil der Vereinigung der [DEBUG\_ADDRESS\_UNION](../../../extensibility/debugger/reference/debug-address-union.md) beim Strukturieren der `dwKind` Feld der `DEBUG_ADDRESS_UNION` Struktur auf festgelegt ist `ADDRESS_KIND_RETVAL` \(ein Wert aus der [ADDRESS\_KIND](../../../extensibility/debugger/reference/address-kind.md) Enumeration\).  
  
## Anforderungen  
 Header: sh.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Siehe auch  
 [Strukturen und Unions](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [DEBUG\_ADDRESS\_UNION](../../../extensibility/debugger/reference/debug-address-union.md)   
 [ADDRESS\_KIND](../../../extensibility/debugger/reference/address-kind.md)