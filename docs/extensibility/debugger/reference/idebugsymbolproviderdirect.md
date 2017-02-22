---
title: "IDebugSymbolProviderDirect | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "IDebugSymbolProviderDirect-Schnittstelle"
ms.assetid: 872b04a8-70de-4ab5-aceb-684c81828545
caps.latest.revision: 6
caps.handback.revision: 6
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugSymbolProviderDirect
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Stellt ein Symbol für, der direkte Zugriff auf die Metadaten und zu den wichtigsten Schnittstellen Symbol verfügt.  
  
## Syntax  
  
```  
IDebugSymbolProviderDirect: IUnknown  
```  
  
## Methoden  
 Diese Schnittstelle implementiert die folgenden Methoden:  
  
|Methode|Beschreibung|  
|-------------|------------------|  
|[GetAppIDFromAddress](../../../extensibility/debugger/reference/idebugsymbolproviderdirect-getappidfromaddress.md)|Ruft den bereitgestellten Bezeichner der Anwendungsdomäne Debug\- Adresse ab.|  
|[GetCurrentModulesInfo](../../../extensibility/debugger/reference/idebugsymbolproviderdirect-getcurrentmodulesinfo.md)|Ruft Informationen über die Module in der Gruppe Symbol ab oder legt diese fest.|  
|[GetCurrentModulesState](../../../extensibility/debugger/reference/idebugsymbolproviderdirect-getcurrentmodulesstate.md)|Ruft Informationen zu der Gruppe Symbol ab, aus der der Symbol für Mitglied ist.|  
|[GetMetaDataImport](../../../extensibility/debugger/reference/idebugsymbolproviderdirect-getmetadataimport.md)|Ruft die Metadaten import Informationen ab.|  
|[GetMethodFromAddress](../../../extensibility/debugger/reference/idebugsymbolproviderdirect-getmethodfromaddress.md)|Ruft Informationen über die Methode auf dem angegebenen debuggen Adresse ab.|  
|[GetSymUnmanagedReader](../../../extensibility/debugger/reference/idebugsymbolproviderdirect-getsymunmanagedreader.md)|Ruft einen Symbolreader für nicht verwalteten Code ab.|  
  
## Hinweise  
 Diese Schnittstelle kann statt den meisten anderen Anbieter Symbol Schnittstellen verwendet werden.  Sie bietet direkten Zugriff auf Metadaten und zum `CorSym`\-Schnittstellen.  
  
## Anforderungen  
 Header: Sh.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll