---
title: "SYMBOL_SEARCH_INFO_FIELDS | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "SYMBOL_SEARCH_INFO_FIELDS"
helpviewer_keywords: 
  - "SYMBOL_SEARCH_INFO_FIELDS-enumeration"
ms.assetid: bce35af0-722d-46d4-afa6-eaae598c51ff
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# SYMBOL_SEARCH_INFO_FIELDS
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Gibt die Art von Symbolinformationen an, der abgerufen werden soll.  
  
## Syntax  
  
```cpp#  
enum enum_SYMBOL_SEARCH_INFO_FIELDS  
{  
   SSIF_NONE                = 0x00000000,  
   SSIF_VERBOSE_SEARCH_INFO = 0x00000001  
};  
typedef DWORD SYMBOL_SEARCH_INFO_FIELDS;  
```  
  
```c#  
public enum enum_SYMBOL_SEARCH_INFO_FIELDS  
{  
   SSIF_NONE                = 0x00000000,  
   SSIF_VERBOSE_SEARCH_INFO = 0x00000001  
};  
  
```  
  
## Mitglieder  
 SSIF\_NONE  
 Gibt keine Flags an  
  
 SSIF\_VERBOSE\_SEARCH\_INFORMATION  
 Gibt alle Suchpfade zurück, die zum Suchen von Symbolen verwendet werden  
  
## Hinweise  
 Diese Flags werden als Parameter übergeben, der ["Getsymbolinfo"](../../../extensibility/debugger/reference/idebugmodule3-getsymbolinfo.md)\-Methode, um die zurückgegebene Menge zu bestimmen.  
  
> [!NOTE]
>  Derzeit wird nur `SSIF_VERBOSE_SEARCH_INFO` unterstützt werden, und es muss als `dwFlags``IDebugModule3::GetSymbolInfo`Parameter angegeben werden.  Alle anderen Werte geben einen Fehler zurück.  
  
## Anforderungen  
 Header: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Siehe auch  
 [Enumerationen](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 ["Getsymbolinfo"](../../../extensibility/debugger/reference/idebugmodule3-getsymbolinfo.md)