---
title: "IDebugAlias | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugAlias"
helpviewer_keywords: 
  - "IDebugAlias-Schnittstelle"
ms.assetid: 3cc4c9a4-7805-4239-b00e-eb4a024f3c55
caps.latest.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 14
---
# IDebugAlias
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

> [!IMPORTANT]
>  In Visual Studio 2015 ist diese Art der Implementierung von ausdrucksauswertungen veraltet. Informationen über das Implementieren von CLR\-ausdrucksauswertungen finden Sie unter [CLR\-Ausdrucksauswertungen](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) und [Managed Expression Evaluator Sample](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Stellt einen numerischen Alias für eine Variable dar. Ein Alias ist einfach einen anderen Namen für eine Variable.  
  
## Syntax  
  
```  
IDebugAlias : IUnknown  
```  
  
## Hinweise für Implementierer  
 Die Auswertung eines Ausdrucks \(EE\) implementiert diese Schnittstelle, um numerische Aliase für Variablen zu unterstützen.  
  
## Hinweise für Aufrufer  
 [CreateAlias](../../../extensibility/debugger/reference/idebugobject2-createalias.md) erstellt einen Alias für ein bestimmtes Objekt. Verwenden Sie zum Suchen von Aliasen [FindAlias](../../../extensibility/debugger/reference/idebugbinder3-findalias.md) oder [GetAllAliases](../../../extensibility/debugger/reference/idebugbinder3-getallaliases.md).  
  
## Methoden in Vtable\-Reihenfolge  
 Die folgenden Methoden definiert werden, dem `IDebugAlias` Schnittstelle.  
  
|Methode|Beschreibung|  
|-------------|------------------|  
|[GetObject](../../../extensibility/debugger/reference/idebugalias-getobject.md)|Ruft das Objekt, auf den dieser Alias verweist.|  
|[GetName](../../../extensibility/debugger/reference/idebugalias-getname.md)|Ruft den Aliasnamen ab.|  
|[GetICorDebugValue](../../../extensibility/debugger/reference/idebugalias-geticordebugvalue.md)|Ruft eine `ICorDebugValue` \-Schnittstelle, die Zugriff auf verwalteten Codeinformationen zu diesem Objekt \(nur verwalteter Code\).|  
|[Dispose](../../../extensibility/debugger/reference/idebugalias-dispose.md)|Kennzeichnet dieses alias als nicht mehr verwendet wird.|  
  
## Hinweise  
 Ein Alias ist eine Dezimalzahl in Form einer Zeichenfolge gefolgt von dem \#\-Zeichen, z. B. 1001\#.  
  
## Anforderungen  
 Header: ee.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Siehe auch  
 [Ausdruck Evaluation\-Schnittstellen](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)   
 [CreateAlias](../../../extensibility/debugger/reference/idebugobject2-createalias.md)   
 [FindAlias](../../../extensibility/debugger/reference/idebugbinder3-findalias.md)   
 [GetAllAliases](../../../extensibility/debugger/reference/idebugbinder3-getallaliases.md)