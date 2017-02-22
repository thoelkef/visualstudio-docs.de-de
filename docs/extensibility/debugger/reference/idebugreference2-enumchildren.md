---
title: "IDebugReference2::EnumChildren | Microsoft Docs"
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
  - "IDebugReference2::EnumChildren"
helpviewer_keywords: 
  - "IDebugReference2::EnumChildren"
ms.assetid: 35b3c2f3-69f4-4013-b555-f847221f62e8
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugReference2::EnumChildren
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Rufen Sie eine Liste der ausgewählten untergeordneten Elementen eines Verweises ab.  Für zukünftige Verwendung reserviert.  
  
## Syntax  
  
```cpp#  
HRESULT EnumChildren (   
   DEBUGREF_INFO_FLAGS        dwFields,  
   DWORD                      dwRadix,  
   DBG_ATTRIB_FLAGS           dwAttribFilter,  
   LPCOLESTR                  pszNameFilter,  
   DWORD                      dwTimeout,  
   IEnumDebugReferenceInfo2** ppEnum  
);  
```  
  
```c#  
int EnumChildren (   
   enum_DEBUGREF_INFO_FLAGS     dwFields,  
   uint                         dwRadix,  
   enum_DBG_ATTRIB_FLAGS        dwAttribFilter,  
   string                       pszNameFilter,  
   uint                         dwTimeout,  
   out IEnumDebugReferenceInfo2 ppEnum  
);  
```  
  
#### Parameter  
 `dwFields`  
 \[in\]  Eine Kombination von Flags aus der [DEBUGREF\_INFO\_FLAGS](../../../extensibility/debugger/reference/debugref-info-flags.md)\-Enumeration, die angibt, welche Felder in den aufgelisteten [DEBUG\_REFERENCE\_INFO](../../../extensibility/debugger/reference/debug-reference-info.md) Strukturen gefüllt werden sollen.  
  
 `dwRadix`  
 \[in\]  Die Basis verwendet werden soll, wenn alle numerischen Daten formatiert werden.  
  
 `dwAttribFilter`  
 \[in\]  Eine Kombination von Flags aus der [DBG\_ATTRIB\_FLAGS](../../../extensibility/debugger/reference/dbg-attrib-flags.md)\-Enumeration, die als Filter `pszNameFilter` in Verbindung mit dem Parameter verwendet wird, um auszuwählen, welche Strukturen aufgelistet werden sollen.  
  
 `pszNameFilter`  
 \[in\]  Eine Zeichenfolge, die einen Filter, z. B. „MyX“ verwendet, `dwAttribFilter` in Verbindung mit dem Parameter, um die Auswahl Strukturen, die aufgelistet werden sollen.  
  
 `dwTimeout`  
 \[in\]  Maximale Zeit in Millisekunden, bevor der Rückgabe dieser Methode zu warten.  `INFINITE` verwenden, um unbegrenzt zu warten.  
  
 `ppEnum`  
 \[out\]  Gibt ein [IEnumDebugReferenceInfo2](../../../extensibility/debugger/reference/ienumdebugreferenceinfo2.md)\-Objekt zurück, das eine Liste der angeforderten untergeordneten Eigenschaften enthält.  
  
## Rückgabewert  
 Gibt immer `E_NOTIMPL` zurück.  
  
## Siehe auch  
 [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)   
 [DEBUGREF\_INFO\_FLAGS](../../../extensibility/debugger/reference/debugref-info-flags.md)   
 [DBG\_ATTRIB\_FLAGS](../../../extensibility/debugger/reference/dbg-attrib-flags.md)   
 [IEnumDebugReferenceInfo2](../../../extensibility/debugger/reference/ienumdebugreferenceinfo2.md)