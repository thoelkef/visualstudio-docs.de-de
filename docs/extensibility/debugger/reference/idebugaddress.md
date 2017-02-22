---
title: "IDebugAddress | Microsoft Docs"
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
  - "IDebugAddress"
helpviewer_keywords: 
  - "IDebugAddress-Schnittstelle"
ms.assetid: bc709ff7-4966-4f36-9af2-690efe2cea1d
caps.latest.revision: 9
caps.handback.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugAddress
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Diese Schnittstelle stellt die Adresse eines Elements dar.  Es wird im Symbol für zurückgegeben.  
  
## Syntax  
  
```  
IDebugAddress : IUnknown  
```  
  
## Hinweise für Implementierer  
 Ein Symbol für implementiert diese Schnittstelle, um eine Adresse eines Objekts darstellt.  
  
## Hinweise für Aufrufer  
 Viele Methoden in zahlreichen Schnittstellen geben diese Schnittstelle zurück.  
  
## Methoden in die Vtable\-Reihenfolge  
 Diese Schnittstelle implementiert die folgende Weise:  
  
|Methode|Beschreibung|  
|-------------|------------------|  
|[GetAddress](../../../extensibility/debugger/reference/idebugaddress-getaddress.md)|Ruft eine [DEBUG\_ADDRESS](../../../extensibility/debugger/reference/debug-address.md) Struktur ab, die ein Objekt und dessen Position beschreibt.|  
  
## Hinweise  
 Der Anbieter Symbol gibt diese Schnittstelle zurück, die ein Objekt und dessen Position innerhalb eines bestimmten Bereichs darstellt \(z. B. Funktion, Methode oder Klasse\).  Diese Schnittstelle wird von zurückgegeben und übergeben den verschiedenen Möglichkeiten des Symbols Anbieters und Ausdrucksauswerters.  Normalerweise ist der Anbieter Symbol als einzige Entität, die den Inhalt dieser Schnittstelle interpretiert werden muss.  
  
## Anforderungen  
 Header: sh.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Siehe auch  
 [Symbol\-Provider\-Schnittstellen](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)   
 [DEBUG\_ADDRESS](../../../extensibility/debugger/reference/debug-address.md)