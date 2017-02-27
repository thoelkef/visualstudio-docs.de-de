---
title: "IDebugProperty2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugProperty2"
helpviewer_keywords: 
  - "IDebugProperty2-Schnittstelle"
ms.assetid: a7d5c70f-a1a5-4120-9f70-184e01c25bff
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# IDebugProperty2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Diese Schnittstelle stellt eine Stapelrahmen dokumenteigenschaft Programm eine Eigenschaft oder eine beliebige andere Eigenschaft dar.  Die Eigenschaft ist gewöhnlich das Ergebnis der Ausdrucksauswertung.  
  
> [!NOTE]
>  Dieser Verwendung von „Eigenschaft“ sollte nicht zu verwechseln mit dieser Bedeutung einer Membervariablen einer Klasse, obwohl `IDebugProperty2` eine solche Entität darstellen kann.  
  
## Syntax  
  
```  
IDebugProperty2 : IUnknown  
```  
  
## Hinweise für Implementierer  
 DE implementiert diese Schnittstelle, um eine bestimmte Weise Wert darstellt.  Beispielsweise könnte der Wert eines numerischen Werts aufgrund einer Ausdrucksauswertung, einem Speicher, der für die Anzeige des Arbeitsspeichers verwendet wurden, oder eine Liste von Registern und deren Werte sein.  
  
## Hinweise für Aufrufer  
 Rufen Sie [EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) oder [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) an, die zum Abrufen dieser Schnittstelle, die das Ergebnis der Auswertung darstellt.  `IDebugExpression2::EvaluateAsync` gibt diese Schnittstelle zurück, indem eine Schnittstelle zum [IDebugExpressionEvaluationCompleteEvent2](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md) SDM sendet, das wiederum [GetResult](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2-getresult.md) aufgerufen wird, um die Eigenschaft abgerufen werden soll.  
  
 [GetDebugProperty](../../../extensibility/debugger/reference/idebugpropertycreateevent2-getdebugproperty.md) gibt diese Schnittstelle zurück, um das zugeordnete Dokument Skript zur Verfügung zu stellen.  
  
 [GetReturnValue](../../../extensibility/debugger/reference/idebugreturnvalueevent2-getreturnvalue.md) gibt diese Schnittstelle zurück, die den Rückgabewert einer Funktion darstellt.  
  
 [GetDebugProperty](../../../extensibility/debugger/reference/idebugprogram2-getdebugproperty.md) gibt diese Schnittstelle zurück, um verschiedene Eigenschaften des Programms z. B. ein Name oder ein Kontext Speicher darzustellen.  
  
 [GetDebugProperty](../../../extensibility/debugger/reference/idebugstackframe2-getdebugproperty.md) gibt diese Schnittstelle zurück, um verschiedene Eigenschaften des Stapelrahmens z. B. lokale Variablen darstellt.  
  
## Methoden in die Vtable\-Reihenfolge  
 In der folgenden Tabelle werden die Methoden von `IDebugProperty2`an.  
  
|Methode|Beschreibung|  
|-------------|------------------|  
|[GetPropertyInfo](../../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md)|Füllt eine [DEBUG\_PROPERTY\_INFO](../../../extensibility/debugger/reference/debug-property-info.md) Struktur aus, die eine Eigenschaft beschreibt.|  
|[SetValueAsString](../../../extensibility/debugger/reference/idebugproperty2-setvalueasstring.md)|Legt den Wert einer Eigenschaft aus einer Zeichenfolge fest.|  
|[SetValueAsReference](../../../extensibility/debugger/reference/idebugproperty2-setvalueasreference.md)|Legt den Wert der Eigenschaft vom Wert eines angegebenen Verweises ab.|  
|[EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md)|Listet die untergeordneten Elemente einer Eigenschaft.|  
|[GetParent](../../../extensibility/debugger/reference/idebugproperty2-getparent.md)|Gibt das übergeordnete Element einer Eigenschaft zurück.|  
|[GetDerivedMostProperty](../../../extensibility/debugger/reference/idebugproperty2-getderivedmostproperty.md)|Gibt die Eigenschaft zurück, die die höchst\-abgeleitete Eigenschaft einer Eigenschaft beschreibt.|  
|[GetMemoryBytes](../../../extensibility/debugger/reference/idebugproperty2-getmemorybytes.md)|Gibt die Bytes an Arbeitsspeicher zurück, die den Wert einer Eigenschaft zusammensetzt.|  
|[GetMemoryContext](../../../extensibility/debugger/reference/idebugproperty2-getmemorycontext.md)|Gibt den Kontext des Arbeitsspeichers für einen Eigenschaftswert zurück.|  
|[GetSize](../../../extensibility/debugger/reference/idebugproperty2-getsize.md)|Gibt die Größe \(in Bytes\) des Eigenschaftswerts zurück.|  
|[\[GetReference](../../../extensibility/debugger/reference/idebugproperty2-getreference.md)|Gibt einen Verweis auf das Wert der Eigenschaft zurück.|  
|[GetExtendedInfo](../../../extensibility/debugger/reference/idebugproperty2-getextendedinfo.md)|Gibt die erweiterten Informationen zu einer Eigenschaft zurück.|  
  
## Hinweise  
 Eine Eigenschaft, die durch eine `IDebugProperty2`\-Schnittstelle dargestellt, kann für einen Wert mit einem Namen, einem Typ und einer Adresse angesehen werden.  In Ausdrücken kann den allgemeineren `IDebugProperty2` alles, das eine Struktur verfügt, mit übergeordneten Elementen und untergeordneten Knoten darstellen.  
  
 Eine Eigenschaft ist vorübergehend und dauert in der Regel nur solange der aktuelle Stapelrahmen, z. B.  Umgekehrt nimmt ein Verweis, z. B. durch eine [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)\-Schnittstelle dargestellt, solange der Wert im Arbeitsspeicher verbleibt.  
  
 Die IDE kann die `IDebugProperty2`\-Schnittstelle verwenden, um Benutzer durchsuchen und Eigenschaften zur Laufzeit geändert werden soll.  
  
## Anforderungen  
 Header: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Siehe auch  
 [Core\-Schnittstellen](../../../extensibility/debugger/reference/core-interfaces.md)   
 [DEBUG\_PROPERTY\_INFO](../../../extensibility/debugger/reference/debug-property-info.md)   
 [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)