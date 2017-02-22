---
title: "DEBUG_CUSTOM_VIEWER | Microsoft Docs"
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
  - "DEBUG_CUSTOM_VIEWER"
helpviewer_keywords: 
  - "DEBUG_CUSTOM_VIEWER-Struktur"
ms.assetid: 8e0ef3f0-0107-48e8-a037-6e52b4c4ed9d
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# DEBUG_CUSTOM_VIEWER
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Eine Struktur, die einen benutzerdefinierten Typ oder eine Viewer schnellansicht identifiziert.  
  
## Syntax  
  
```cpp  
typedef struct tagDEBUG_CUSTOM_VIEWER {  
   DWORD dwID;  
   BSTR  bstrMenuName;  
   BSTR  bstrDescription;  
   GUID  guidLang;  
   GUID  guidVendor;  
   BSTR  bstrMetric;  
} DEBUG_CUSTOM_VIEWER;  
```  
  
```c#  
public struct DEBUG_CUSTOM_VIEWER {  
   public uint   dwID;  
   public string bstrMenuName;  
   public string bstrDescription;  
   public Guid   guidLang;  
   public Guid   guidVendor;  
   public string bstrMetric;  
};  
```  
  
## Mitglieder  
 dwID  
 Eine ID, die aus mehreren Viewern oder Schnellansichten über ein `GUID`implementiert werden.  
  
 bstrMenuName  
 Der Text, der im Dropdownmenü angezeigt wird.  
  
 bstrDescription  
 Eine Beschreibung des benutzerdefinierten Viewers oder der Typ schnellansicht, muss ein NULL\-Wert sein \(wenn nicht verwendet\).  
  
 guidLang  
 Sprache des ausdrucksauswerters erfüllt, oder legt diesen fest.  
  
 guidVendor  
 ausdrucksauswerters des Anbieters erfüllt, oder legt diesen fest.  
  
 bstrMetric  
 Metrik, mit der der benutzerdefinierte Typ oder der Viewer schnellansicht `CLSID` gespeichert wird.  
  
## Hinweise  
 Eine Liste dieser Struktur wird von einem Aufruf der [GetCustomViewerList](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md)\-Methode zurückgegeben \(und, die zur Erweiterung [GetCustomViewerList](../../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewerlist.md)\-Methode\).  
  
## Anforderungen  
 Header: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Siehe auch  
 [Strukturen und Unions](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [GetCustomViewerList](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md)   
 [GetCustomViewerList](../../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewerlist.md)