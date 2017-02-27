---
title: "IDebugObject2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugObject2"
helpviewer_keywords: 
  - "IDebugObject2-Schnittstelle"
ms.assetid: ef640967-8adb-4793-994d-ae1736510891
caps.latest.revision: 15
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 15
---
# IDebugObject2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

> [!IMPORTANT]
>  In Visual Studio 2015 ist diese Art der Implementierung von ausdrucksauswertungen veraltet. Informationen über das Implementieren von CLR\-ausdrucksauswertungen finden Sie unter [CLR\-Ausdrucksauswertungen](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) und [Managed Expression Evaluator Sample](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Diese Schnittstelle bietet zusätzliche Informationen zu einem Objekt.  
  
## Syntax  
  
```  
IDebugObject2 : IDebugObject  
```  
  
## Hinweise für Implementierer  
 Die Auswertung eines Ausdrucks implementiert diese Schnittstelle, um Unterstützung für Aliase und Zugriff auf Informationen über das Objekt.  
  
## Hinweise für Aufrufer  
 Eine [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) Schnittstelle kann mithilfe dieser Schnittstelle abrufen [QueryInterface](/visual-cpp/atl/queryinterface). Darüber hinaus [GetObject](../../../extensibility/debugger/reference/idebugalias-getobject.md) gibt diese Schnittstelle.  
  
## Methoden in Vtable\-Reihenfolge  
 Zusätzlich zu den Methoden für die [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) \-Schnittstelle, die `IDebugObject2` \-Schnittstelle implementiert die folgenden:  
  
|Methode|Beschreibung|  
|-------------|------------------|  
|[GetBackingFieldForProperty](../../../extensibility/debugger/reference/idebugobject2-getbackingfieldforproperty.md)|Ruft das Feld oder die Variable \(sofern vorhanden\), die von diesem Objekt dargestellte Eigenschaft sichern.|  
|[GetICorDebugValue](../../../extensibility/debugger/reference/idebugobject2-geticordebugvalue.md)|Ruft das verwaltete Codeobjekt, der den Wert dieses Objekts ab.|  
|[CreateAlias](../../../extensibility/debugger/reference/idebugobject2-createalias.md)|Erstellt eine eindeutige ID für dieses Objekt oder einen vorhandenen Alias gibt.|  
|[GetAlias](../../../extensibility/debugger/reference/idebugobject2-getalias.md)|Ruft die diesem Objekt zugeordneten Alias ab, sofern vorhanden.|  
|[GetField](../../../extensibility/debugger/reference/idebugobject2-getfield.md)|Ruft den Typ des Objekts ab.|  
|[IsUserData](../../../extensibility/debugger/reference/idebugobject2-isuserdata.md)|Bestimmt, ob dieses Objekt auf Benutzerdaten darstellt.|  
|[IsEncOutdated](../../../extensibility/debugger/reference/idebugobject2-isencoutdated.md)|Bestimmt, ob der Status von bearbeiten und Fortfahren nicht mehr gültig ist.<br /><br /> Eine benutzerdefinierte Ausdrucksauswerter implementiert diese Methode nicht \(sollte immer zurückgegeben `E_NOTIMPL`\).|  
  
## Hinweise  
 Finden Sie unter [IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md) ausführliche Informationen zu Aliasen.  
  
## Anforderungen  
 Header: ee.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Siehe auch  
 [Ausdruck Evaluation\-Schnittstellen](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)   
 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)   
 [IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md)   
 [GetObject](../../../extensibility/debugger/reference/idebugalias-getobject.md)