---
title: "IDebugGenericFieldInstance | Microsoft Docs"
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
  - "IDebugGenericFieldInstance-Schnittstelle"
ms.assetid: f68b4761-be8b-4801-9d4b-cde90e01d95e
caps.latest.revision: 7
caps.handback.revision: 7
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugGenericFieldInstance
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Stellt eine Instanz eines Felds für einen verwalteten Code generischen Typ dar.  
  
## Syntax  
  
```  
IDebugGenericFieldInstance : IUnknown  
```  
  
## Methoden  
 Diese Schnittstelle implementiert die folgenden Methoden:  
  
|Methode|Beschreibung|  
|-------------|------------------|  
|[GetTypeArguments](../../../extensibility/debugger/reference/idebuggenericfieldinstance-gettypearguments.md)|Ruft die Typparameter Argumente für diese Instanz ab.|  
|[TypeArgumentCount](../../../extensibility/debugger/reference/idebuggenericfieldinstance-typeargumentcount.md)|Gibt die Anzahl der Typparameter argumenten für diese Instanz zurück.|  
  
## Anforderungen  
 Header: Sh.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll