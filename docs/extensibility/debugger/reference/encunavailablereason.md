---
title: "EncUnavailableReason | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "EncUnavailableReason"
helpviewer_keywords: 
  - "EncUnavailableReason-enumeration"
ms.assetid: c10aa4c0-d7e0-4de1-b8ff-7e050985eb12
caps.latest.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 8
---
# EncUnavailableReason
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

`This is for internal use only!` stellt die Gründe veranschaulicht, dass **Bearbeiten und Fortfahren** nicht verfügbar ist.  
  
## Syntax  
  
```cpp#  
enum tagEncUnavailableReason {  
   ENCUN_NONE,  
   ENCUN_INTEROP,  
   ENCUN_SQLCLR,  
   ENCUN_MINIDUMP,  
   ENCUN_EMBEDDED,  
   ENCUN_ATTACH,  
   ENCUN_WIN64  
};  
typedef enum tagEncUnavailableReason EncUnavailableReason;  
```  
  
```c#  
public enum EncUnavailableReason {  
   ENCUN_NONE,  
   ENCUN_INTEROP,  
   ENCUN_SQLCLR,  
   ENCUN_MINIDUMP,  
   ENCUN_EMBEDDED,  
   ENCUN_ATTACH,  
   ENCUN_WIN64  
};  
```  
  
#### Parameter  
 ENCUN\_NONE  
 Es wurde kein bestimmter Grund für das Bearbeiten und Fortfahren nicht verfügbar ist.  
  
 ENCUN\_INTEROP  
 Bearbeiten und Fortfahren kann nicht bei einem Aufruf einer Interop verfügbar.  
  
 ENCUN\_SQLCLR  
 Bearbeiten und Fortfahren kann nicht innerhalb eines SQL\-Prozeduraufrufs verfügbar, der von der Common Language Runtime \(CLR\) verwendet.  
  
 ENCUN\_MINIDUMP  
 Bearbeiten und Fortfahren kann nicht beim Verarbeiten von Mini DUMP verfügbar.  
  
 ENCUN\_EMBEDDED  
 Bearbeiten und Fortfahren ist nicht verfügbar, wenn diese eingebetteten Code verarbeiten.  
  
 ENCUN\_ATTACH  
 Bearbeiten und Fortfahren ist nicht verfügbar, da die Sitzung angefügt wurde, nicht wieder gestartet, der Debugger.  
  
 ENCUN\_WIN64  
 Bearbeiten und Fortfahren kann nicht beim Verarbeiten von 64\-Bit\-Windows\-Code verfügbar.  
  
## Hinweise  
 Diese Enumeration ist nur für die interne Verwendung durch [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)].  Die [GetENCAvailableState](../../../extensibility/debugger/reference/idebugprocess3-getencavailablestate.md) und [DisableENC](../../../extensibility/debugger/reference/idebugprocess3-disableenc.md)\-Methoden, z. B. von einem benutzerdefinierten Anschlusslieferanten implementiert `E_NOTIMPL`sollten immer zurückgeben.  
  
## Anforderungen  
 Header: msdbg.idl  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Siehe auch  
 [Enumerationen](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [DisableENC](../../../extensibility/debugger/reference/idebugprocess3-disableenc.md)   
 [GetENCAvailableState](../../../extensibility/debugger/reference/idebugprocess3-getencavailablestate.md)