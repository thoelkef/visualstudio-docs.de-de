---
title: "IDebugStackFrame2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugStackFrame2"
helpviewer_keywords: 
  - "IDebugStackFrame2-Schnittstelle"
ms.assetid: bd212a6a-dcc6-4756-a77a-e8dfda38b104
caps.latest.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 14
---
# IDebugStackFrame2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Diese Schnittstelle stellt einen einzelnen Stapelrahmen in einer Aufrufliste in einem bestimmten Thread dar.  
  
## Syntax  
  
```  
IDebugStackFrame2 : IUnknown  
```  
  
## Hinweise für Implementierer  
 Das Debugmodul \(DE\) implementiert diese Schnittstelle, um einen Stapelrahmen darstellt.  
  
## Hinweise für Aufrufer  
 Aufruf [EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md) , um eine [IEnumDebugFrameInfo2](../../../extensibility/debugger/reference/ienumdebugframeinfo2.md)\-Schnittstelle abzurufen.  Rufen Sie [Weiter](../../../extensibility/debugger/reference/ienumdebugframeinfo2-next.md) auf, um eine [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) Struktur abzurufen, die die `IDebugStackFrame2`\-Schnittstelle enthält.  
  
## Methoden in die Vtable\-Reihenfolge  
 In der folgenden Tabelle werden die Methoden von `IDebugStackFrame2`an.  
  
|Methode|Beschreibung|  
|-------------|------------------|  
|[GetCodeContext](../../../extensibility/debugger/reference/idebugstackframe2-getcodecontext.md)|Ruft den Kontext des Codes für diesen Stapelrahmen ab.|  
|[GetDocumentContext](../../../extensibility/debugger/reference/idebugstackframe2-getdocumentcontext.md)|Ruft den Dokumentenkontext für diesen Stapelrahmen ab.|  
|[GetName](../../../extensibility/debugger/reference/idebugstackframe2-getname.md)|Ruft den Namen des Stapelrahmens ab.|  
|[GetInfo](../../../extensibility/debugger/reference/idebugstackframe2-getinfo.md)|Ruft eine Beschreibung des Stapelrahmens ab.|  
|[GetPhysicalStackRange](../../../extensibility/debugger/reference/idebugstackframe2-getphysicalstackrange.md)|Ruft eine Darstellung des abhängigen MACHINE des Bereichs der physikalischen Adressen ab, die einem Stapelrahmen zugeordnet sind.|  
|[GetExpressionContext](../../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md)|Ruft einen Auswertungs Elementkontext für das diese der Ausdrucksauswertung innerhalb des aktuellen Kontexts eines Stapelrahmens und des Threads ab.|  
|[GetLanguageInfo](../../../extensibility/debugger/reference/idebugstackframe2-getlanguageinfo.md)|Ruft die Sprache ab, die einem Stapelrahmen zugeordnet ist.|  
|[GetDebugProperty](../../../extensibility/debugger/reference/idebugstackframe2-getdebugproperty.md)|Ruft eine Beschreibung der Eigenschaften ab, die einem Stapelrahmen zugeordnet sind.|  
|[\[EnumProperties](../../../extensibility/debugger/reference/idebugstackframe2-enumproperties.md)|Erstellt einen Enumerator für Stapelrahmen Properties.|  
|[GetThread](../../../extensibility/debugger/reference/idebugstackframe2-getthread.md)|Ruft den Thread ab, der einem Stapelrahmen zugeordnet ist.|  
  
## Hinweise  
 Diese Schnittstelle wird erhalten nur, wenn das Programm, das gedebuggt wird, an einem Haltepunkt angehalten wurde \(entweder verursacht durch einen USER\-festgelegten Haltepunkt oder eine Ausnahme\).  Von dieser Schnittstelle kann ein Ausdruckskontext abgerufen werden, um Ausdrücke auswerten, kann eine Liste von Registern zurückgegeben werden, oder die Aufrufliste kann abgerufen und überprüft werden.  
  
## Anforderungen  
 Header: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Siehe auch  
 [Core\-Schnittstellen](../../../extensibility/debugger/reference/core-interfaces.md)