---
title: "IDebugSourceServerModule | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "IDebugSourceServerModule-Schnittstelle"
ms.assetid: 38213060-451d-46e6-8b4a-efc123e01a2c
caps.latest.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugSourceServerModule
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Der Quellserver Stellt die Informationen dar, die in einer PDB\-Datei enthalten ist.  
  
## Syntax  
  
```  
IDebugSourceServerModule : IUnknown  
```  
  
## Hinweise für Implementierer  
 Diese Schnittstelle wird von Debugger module implementiert und verwendet vom Debugger Benutzeroberfläche.  
  
## Methoden  
 In der folgenden Tabelle werden die Methoden von `IDebugSourceServerModule`an.  
  
|Methode|Beschreibung|  
|-------------|------------------|  
|[GetSourceServerData](../../../extensibility/debugger/reference/idebugsourceservermodule-getsourceserverdata.md)|Ruft ein Array von Quellserver Informationen ab.|  
  
## Anforderungen  
 Header: Msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll