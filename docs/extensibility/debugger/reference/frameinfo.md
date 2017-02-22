---
title: "FRAMEINFO | Microsoft Docs"
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
  - "FRAMEINFO"
helpviewer_keywords: 
  - "FRAMEINFO-Struktur"
ms.assetid: 95001b89-dddb-45bb-889d-8327994e38a5
caps.latest.revision: 8
caps.handback.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
---
# FRAMEINFO
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Beschreibt einen Stapelrahmen.  
  
## Syntax  
  
```cpp#  
typedef struct tagFRAMEINFO {   
   FRAMEINFO_FLAGS    m_dwValidFields;  
   BSTR               m_bstrFuncName;  
   BSTR               m_bstrReturnType;  
   BSTR               m_bstrArgs;  
   BSTR               m_bstrLanguage;  
   BSTR               m_bstrModule;  
   UINT64             m_addrMin;  
   UINT64             m_addrMax;  
   IDebugStackFrame2* m_pFrame;  
   IDebugModule2*     m_pModule;  
   BOOL               m_fHasDebugInfo;  
   BOOL               m_fStaleCode;  
   BOOL               m_fAnnotatedFrame;  
} FRAMEINFO;  
```  
  
```c#  
public struct FRAMEINFO {   
   public uint              m_dwValidFields;  
   public string            m_bstrFuncName;  
   public string            m_bstrReturnType;  
   public string            m_bstrArgs;  
   public string            m_bstrLanguage;  
   public string            m_bstrModule;  
   public ulong             m_addrMin;  
   public ulong             m_addrMax;  
   public IDebugStackFrame2 m_pFrame;  
   public IDebugModule2     m_pModule;  
   public int               m_fHasDebugInfo;  
   public int               m_fStaleCode;  
   public int               m_fAnnotatedFrame;  
} FRAMEINFO;  
```  
  
## Mitglieder  
 m\_dwValidFields  
 Eine Kombination von Flags aus der [FRAMEINFO\_FLAGS](../../../extensibility/debugger/reference/frameinfo-flags.md)\-Enumeration, die angibt, welche Felder aufgefüllt werden.  
  
 m\_bstrFuncName  
 Der Funktionsname, die dem Stapelrahmen.  
  
 m\_bstrReturnType  
 Der Rückgabetyp dem Stapelrahmen zugeordnet ist.  
  
 m\_bstrArgs  
 Die Argumente für die Funktion, die dem Stapelrahmen.  
  
 m\_bstrLanguage  
 Die Sprache, in der die Funktion implementiert wird.  
  
 m\_bstrModule  
 Der Modulname dem Stapelrahmen zugeordnet ist.  
  
 m\_addrMin  
 Die minimale physische Stapeladresse.  
  
 m\_addrMAX  
 Die maximale physikalische Stapeladresse.  
  
 m\_pFrame  
 Das [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)\-Objekt, das diesen Stapelrahmen darstellt.  
  
 m\_pFrame  
 Das [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md)\-Objekt, das das Modul darstellt, die diesen Stapelrahmen enthält.  
  
 m\_fHasDebugInfo  
 Ein Wert ungleich 0 \(`TRUE`\), wenn Debuginformationen in den angegebenen Rahmen vorhanden sind.  
  
 m\_fHasDebugInfo  
 Ein Wert ungleich 0 \(`TRUE`\) Wenn der Stapelrahmen mit dem Code zugeordnet ist, der nicht mehr gültig ist.  
  
 m\_fHasDebugInfo  
 Ein Wert ungleich 0 \(`TRUE`\) Wenn der Stapelrahmen vom Manager der Sitzung Debuggen \(SDM\) mit Anmerkungen versehen wird.  
  
## Hinweise  
 Diese Struktur wird auf die gefüllt werden soll [GetInfo](../../../extensibility/debugger/reference/idebugstackframe2-getinfo.md)\-Methode übergeben.  Diese Struktur wird ebenfalls in einer Liste enthalten, auf die in der [IEnumDebugFrameInfo2](../../../extensibility/debugger/reference/ienumdebugframeinfo2.md)\-Schnittstelle enthalten ist, die wiederum von einem Aufruf der [EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md)\-Methode zurückgegeben wird.  
  
## Anforderungen  
 Header: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Siehe auch  
 [Strukturen und Unions](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [FRAMEINFO\_FLAGS](../../../extensibility/debugger/reference/frameinfo-flags.md)   
 [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)   
 [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md)   
 [GetInfo](../../../extensibility/debugger/reference/idebugstackframe2-getinfo.md)   
 [IEnumDebugFrameInfo2](../../../extensibility/debugger/reference/ienumdebugframeinfo2.md)   
 [EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md)