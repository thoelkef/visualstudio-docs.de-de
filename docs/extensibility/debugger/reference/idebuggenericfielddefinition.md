---
title: "IDebugGenericFieldDefinition | Microsoft Docs"
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
  - "IDebugGenericFieldDefinition-Schnittstelle"
ms.assetid: b5a853b7-221e-4d62-8948-07423089d75d
caps.latest.revision: 7
caps.handback.revision: 7
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugGenericFieldDefinition
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Stellt die Definition eines Felds für einen verwalteten Code generischen Typ dar.  
  
## Syntax  
  
```  
IDebugGenericFieldDefinition : IUnknown  
```  
  
## Methoden  
 Diese Schnittstelle implementiert die folgenden Methoden:  
  
|Methode|Beschreibung|  
|-------------|------------------|  
|[ConstructInstantiation](../../../extensibility/debugger/reference/idebuggenericfielddefinition-constructinstantiation.md)|Erstellt eine Instanz des angegebenen Felds ein Array von Typargumenten.|  
|[GetFormalTypeParams](../../../extensibility/debugger/reference/idebuggenericfielddefinition-getformaltypeparams.md)|Ruft die angegebenen Parameter die Anzahl von Parametern ab.|  
|[TypeParamCount](../../../extensibility/debugger/reference/idebuggenericfielddefinition-typeparamcount.md)|Ruft die Anzahl von Typparametern ab, die mit dem generischen Feld zugeordnet werden.|  
  
## Anforderungen  
 Header: Sh.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll