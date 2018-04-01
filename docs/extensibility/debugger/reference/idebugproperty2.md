---
title: IDebugProperty2 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugProperty2
helpviewer_keywords:
- IDebugProperty2 interface
ms.assetid: a7d5c70f-a1a5-4120-9f70-184e01c25bff
caps.latest.revision: 11
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 8dc1305fb8534dc8e14192268913290aef25f2cc
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="idebugproperty2"></a>IDebugProperty2
Diese Schnittstelle darstellt eine Stack-Frame-Eigenschaft, eine Dokumenteigenschaft Programm oder eine andere Eigenschaft. Die Eigenschaft ist in der Regel das Ergebnis der Auswertung von Ausdrücken.  
  
> [!NOTE]
>  Diese Verwendung von "Property" dürfen nicht mit, d. h. einer Klasse, einer Membervariable verwechselt werden, obwohl ein `IDebugProperty2` können solche Entität darstellen.  
  
## <a name="syntax"></a>Syntax  
  
```  
IDebugProperty2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Hinweise für Implementierer  
 Die DE implementiert diese Schnittstelle, um eine bestimmte Art von Wert darstellen. Der Wert kann z. B. einen numerischen Wert als Ergebnis eine Auswertung von Ausdrücken, eine Speicherkontext zum Anzeigen von Arbeitsspeicher oder eine Liste von Registern und deren Werten sein.  
  
## <a name="notes-for-callers"></a>Hinweise für Aufrufer  
 Rufen Sie [EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) oder [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) beim Abrufen von dieser Schnittstelle das Ergebnis eine Auswertung dar. `IDebugExpression2::EvaluateAsync`gibt diese Schnittstelle durch Senden einer [IDebugExpressionEvaluationCompleteEvent2](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md) Schnittstelle, um die SDM, die ihrerseits [GetResult](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2-getresult.md) beim Abrufen einer Eigenschaft.  
  
 [GetDebugProperty](../../../extensibility/debugger/reference/idebugpropertycreateevent2-getdebugproperty.md) gibt diese Schnittstelle, um das zugeordnete Skriptdokument zur Verfügung.  
  
 [GetReturnValue](../../../extensibility/debugger/reference/idebugreturnvalueevent2-getreturnvalue.md) gibt diese Schnittstelle, um den Rückgabewert einer Funktion darstellen.  
  
 [GetDebugProperty](../../../extensibility/debugger/reference/idebugprogram2-getdebugproperty.md) gibt diese Schnittstelle, um verschiedene Eigenschaften des Programms wie z. B. einen Namen oder eine Arbeitsspeicher-Kontext darstellen.  
  
 [GetDebugProperty](../../../extensibility/debugger/reference/idebugstackframe2-getdebugproperty.md) gibt diese Schnittstelle, um verschiedene Eigenschaften des Stapelrahmens z. B. lokale Variablen darstellen.  
  
## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge  
 Die folgende Tabelle zeigt die Methoden der `IDebugProperty2`.  
  
|Methode|Beschreibung|  
|------------|-----------------|  
|[GetPropertyInfo](../../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md)|Füllt eine [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md) -Struktur, die eine Eigenschaft beschreibt.|  
|[SetValueAsString](../../../extensibility/debugger/reference/idebugproperty2-setvalueasstring.md)|Legt den Wert einer Eigenschaft aus einer Zeichenfolge fest.|  
|[SetValueAsReference](../../../extensibility/debugger/reference/idebugproperty2-setvalueasreference.md)|Legt den Wert der Eigenschaft aus dem Wert eines bestimmten Verweises fest.|  
|[EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md)|Listet die untergeordneten Elemente einer Eigenschaft an.|  
|[GetParent](../../../extensibility/debugger/reference/idebugproperty2-getparent.md)|Gibt das übergeordnete Element einer Eigenschaft zurück.|  
|[GetDerivedMostProperty](../../../extensibility/debugger/reference/idebugproperty2-getderivedmostproperty.md)|Gibt die Eigenschaft, die beschreibt, die am meisten abgeleiteten-Eigenschaft einer Eigenschaft zurück.|  
|[GetMemoryBytes](../../../extensibility/debugger/reference/idebugproperty2-getmemorybytes.md)|Gibt die Speicherbytes an, die den Wert einer Eigenschaft zu bilden.|  
|[GetMemoryContext](../../../extensibility/debugger/reference/idebugproperty2-getmemorycontext.md)|Gibt den Arbeitsspeicher-Kontext für einen Eigenschaftswert zurück.|  
|[GetSize](../../../extensibility/debugger/reference/idebugproperty2-getsize.md)|Gibt die Größe in Bytes, der den Wert der Eigenschaft zurück.|  
|[GetReference](../../../extensibility/debugger/reference/idebugproperty2-getreference.md)|Gibt einen Verweis auf den Wert dieser Eigenschaft zurück.|  
|[GetExtendedInfo](../../../extensibility/debugger/reference/idebugproperty2-getextendedinfo.md)|Gibt den erweiterten Informationen einer Eigenschaft zurück.|  
  
## <a name="remarks"></a>Hinweise  
 Eine Eigenschaft, dargestellt durch eine `IDebugProperty2` Schnittstellen, kann als Wert mit einem Namen, einen Typ und eine Adresse betrachtet werden. Allgemeiner ausgedrückt ein `IDebugProperty2` können darstellen, das eine hierarchische Struktur, mit übergeordneten und untergeordneten Knoten.  
  
 Eine Eigenschaft ist in der Regel um ein vorübergehendes, z. B. dauert nur so lange als den aktuellen Stapelrahmen. Andererseits, einen Verweis, dargestellt durch eine [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md) Schnittstelle, dauert, als der Wert im Arbeitsspeicher bleibt.  
  
 Die IDE können Sie die `IDebugProperty2` Schnittstelle, damit Benutzer suchen und Ändern von Eigenschaften zur Laufzeit.  
  
## <a name="requirements"></a>Anforderungen  
 Header: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Siehe auch  
 [Core-Schnittstellen](../../../extensibility/debugger/reference/core-interfaces.md)   
 [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md)   
 [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)