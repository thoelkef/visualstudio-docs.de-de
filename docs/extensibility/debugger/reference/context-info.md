---
title: "CONTEXT_INFO | Microsoft Docs"
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
  - "CONTEXT_INFO"
helpviewer_keywords: 
  - "CONTEXT_INFO-Struktur"
ms.assetid: 6b513f4e-e7b0-4969-adf0-2205ccc1e09b
caps.latest.revision: 11
caps.handback.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
---
# CONTEXT_INFO
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Diese Struktur beschreibt einen Speicher Elementkontext oder Code Elementkontext.  
  
## Syntax  
  
```cpp#  
typedef struct _tagCONTEXT_INFO {   
   CONTEXT_INFO_FIELDS dwFields;  
   BSTR                bstrModuleUrl;  
   BSTR                bstrFunction;  
   TEXT_POSITION       posFunctionOffset;  
   BSTR                bstrAddress;  
   BSTR                bstrAddressOffset;  
   BSTR                bstrAddressAbsolute;  
} CONTEXT_INFO;  
```  
  
```c#  
public struct CONTEXT_INFO {  
   public uint          dwFields;  
   public string        bstrModuleUrl;  
   public string        bstrFunction;  
   public TEXT_POSITION posFunctionOffset;  
   public string        bstrAddress;  
   public string        bstrAddressOffset;  
   public string        bstrAddressAbsolute;  
};  
```  
  
## Mitglieder  
 dwFields  
 Eine Kombination von Flags aus dieser [CONTEXT\_INFO\_FIELDS](../../../extensibility/debugger/reference/context-info-fields.md)\-Enumeration, die angibt, welche Felder sind**.**ergänztes  
  
 bstrModuleUrl  
 Der Name des Moduls, in dem der Kontext befindet.  
  
 bstrFunction  
 Der Funktionsname, in dem der Kontext befindet.  
  
 posFunctionOffset  
 Eine [TEXT\_POSITION](../../../extensibility/debugger/reference/text-position.md) Struktur, die den Zeilen\- und Spaltenoffset der Funktion identifiziert, die dem Code Elementkontext zugeordnet ist.  
  
 bstrAddress  
 Die Adresse im Code, wobei der angegebene Kontext befindet.  
  
 bstrAddressOffset  
 Der Offset der Adresse im Code, wobei der angegebene Kontext befindet.  
  
 bstrAddressAbsolute  
 Die absolute Adresse im Arbeitsspeicher, wobei der angegebene Kontext befindet.  
  
## Hinweise  
 Diese Struktur wird von einem Aufruf der [GetInfo](../../../extensibility/debugger/reference/idebugmemorycontext2-getinfo.md)\-Methode zurückgegeben.  
  
 Ein typisches Anwendungsbeispiel für diese Struktur ist zur Unterstützung eines Fensters Debuggen **Arbeitsspeicher** .  
  
## Anforderungen  
 Header: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Siehe auch  
 [Strukturen und Unions](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [GetInfo](../../../extensibility/debugger/reference/idebugmemorycontext2-getinfo.md)   
 [CONTEXT\_INFO\_FIELDS](../../../extensibility/debugger/reference/context-info-fields.md)   
 [TEXT\_POSITION](../../../extensibility/debugger/reference/text-position.md)