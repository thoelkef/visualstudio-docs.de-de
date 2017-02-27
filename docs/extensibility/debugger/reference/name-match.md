---
title: "NAME_MATCH | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "NAME_MATCH"
helpviewer_keywords: 
  - "NAME_MATCH-enumeration"
ms.assetid: 3842c417-a3c9-4259-a05f-52b64b829ef6
caps.latest.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 8
---
# NAME_MATCH
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Wählt die Option Groß\-\/Kleinschreibung für Vergleiche von Namen aus.  
  
## Syntax  
  
```cpp#  
typedef enum {   
   nmNone            = 0,  
   nmCaseSensitive   = 1,  
   nmCaseInsensitive = 2  
} NAME_MATCH;  
```  
  
```c#  
public enum NameMatchOptions {   
   nmNone            = 0,  
   nmCaseSensitive   = 1,  
   nmCaseInsensitive = 2  
}  
```  
  
## Mitglieder  
 nmNone  
 Es wurden keine Optionen angegeben.  
  
 nmCaseSensitive  
 Gibt an, dass die Namen, um übereinstimmende ist die Groß\- und Kleinschreibung berücksichtigt wird.  
  
 nmCaseInsensitive  
 Gibt an, dass die Namen, um übereinstimmende Groß\-\/Kleinschreibung nicht beachtet werden soll.  
  
## Hinweise  
 Übergabe als Argument an den folgenden Methoden:  
  
-   [GetTypeByName](../../../extensibility/debugger/reference/idebugsymbolprovider-gettypebyname.md)  
  
-   [GetClassTypeByName](../../../extensibility/debugger/reference/idebugsymbolprovider-getclasstypebyname.md)  
  
-   [\[EnumFields](../../../extensibility/debugger/reference/idebugcontainerfield-enumfields.md)  
  
-   [GetMethodFieldsByName](../../../extensibility/debugger/reference/idebugsymbolprovider-getmethodfieldsbyname.md)  
  
## Anforderungen  
 Header: sh.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Siehe auch  
 [Enumerationen](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [GetTypeByName](../../../extensibility/debugger/reference/idebugsymbolprovider-gettypebyname.md)   
 [GetClassTypeByName](../../../extensibility/debugger/reference/idebugsymbolprovider-getclasstypebyname.md)   
 [\[EnumFields](../../../extensibility/debugger/reference/idebugcontainerfield-enumfields.md)   
 [GetMethodFieldsByName](../../../extensibility/debugger/reference/idebugsymbolprovider-getmethodfieldsbyname.md)