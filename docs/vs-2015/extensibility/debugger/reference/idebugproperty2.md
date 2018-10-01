---
title: IDebugProperty2 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
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
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 8c728c2e4955d35e2954fbda0a4a4432c550666d
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47522533"
---
# <a name="idebugproperty2"></a>IDebugProperty2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [IDebugProperty2](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugproperty2).  
  
Diese Schnittstelle stellt eine Stack-Frame-Eigenschaft, einer Dokumenteigenschaft Programm oder eine andere Eigenschaft. Die Eigenschaft ist in der Regel das Ergebnis der Auswertung eines Ausdrucks.  
  
> [!NOTE]
>  Diese Verwendung von "Property" dürfen nicht verwechselt werden mit, d. h. einer Membervariablen einer Klasse, obwohl ein `IDebugProperty2` können solche Entität darstellen.  
  
## <a name="syntax"></a>Syntax  
  
```  
IDebugProperty2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Hinweise für Implementierer  
 Die DE implementiert diese Schnittstelle, um eine bestimmte Art von Wert darstellen. Der Wert kann z. B. einen numerischen Wert als Ergebnis der Auswertung eines Ausdrucks, einen Speicherkontext, der zum Anzeigen von Arbeitsspeicher oder eine Liste der Register und deren Werte sein.  
  
## <a name="notes-for-callers"></a>Hinweise für Aufrufer  
 Rufen Sie [EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) oder [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) auf diesem-Schnittstelle abzurufen, die das Ergebnis einer Auswertung darstellt. `IDebugExpression2::EvaluateAsync` Diese Schnittstelle gibt, durch Senden einer [IDebugExpressionEvaluationCompleteEvent2](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md) Schnittstelle, das SDM, das wiederum aufruft [GetResult](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2-getresult.md) beim Abrufen einer Eigenschaft.  
  
 [GetDebugProperty](../../../extensibility/debugger/reference/idebugpropertycreateevent2-getdebugproperty.md) gibt diese Schnittstelle, um die zugehörigen Skript-Dokument bereit.  
  
 [GetReturnValue](../../../extensibility/debugger/reference/idebugreturnvalueevent2-getreturnvalue.md) gibt diese Schnittstelle, um den Rückgabewert einer Funktion darstellen.  
  
 [GetDebugProperty](../../../extensibility/debugger/reference/idebugprogram2-getdebugproperty.md) gibt diese Schnittstelle, um verschiedene Eigenschaften des Programms wie z. B. einen Namen oder einen Speicherkontext darstellen.  
  
 [GetDebugProperty](../../../extensibility/debugger/reference/idebugstackframe2-getdebugproperty.md) gibt diese Schnittstelle, um verschiedene Eigenschaften des Stapelrahmens wie z. B. lokale Variablen darstellen.  
  
## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge  
 Die folgende Tabelle zeigt die Methoden der `IDebugProperty2`.  
  
|Methode|Beschreibung|  
|------------|-----------------|  
|[GetPropertyInfo](../../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md)|Füllt ein [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md) -Struktur, die eine Eigenschaft beschreibt.|  
|[SetValueAsString](../../../extensibility/debugger/reference/idebugproperty2-setvalueasstring.md)|Legt den Wert einer Eigenschaft aus einer Zeichenfolge fest.|  
|[SetValueAsReference](../../../extensibility/debugger/reference/idebugproperty2-setvalueasreference.md)|Legt den Wert der Eigenschaft aus dem Wert eines angegebenen Verweises.|  
|[EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md)|Listet die untergeordneten Elemente einer Eigenschaft an.|  
|[GetParent](../../../extensibility/debugger/reference/idebugproperty2-getparent.md)|Gibt das übergeordnete Element eine Eigenschaft zurück.|  
|[GetDerivedMostProperty](../../../extensibility/debugger/reference/idebugproperty2-getderivedmostproperty.md)|Gibt die Eigenschaft, die beschreibt, die am stärksten abgeleiteten-Eigenschaft einer Eigenschaft zurück.|  
|[GetMemoryBytes](../../../extensibility/debugger/reference/idebugproperty2-getmemorybytes.md)|Gibt zurück, die Arbeitsspeicher-Bytes, aus die den Wert einer Eigenschaft zusammensetzt.|  
|[GetMemoryContext](../../../extensibility/debugger/reference/idebugproperty2-getmemorycontext.md)|Gibt den Arbeitsspeicher-Kontext für einen Eigenschaftswert zurück.|  
|[GetSize](../../../extensibility/debugger/reference/idebugproperty2-getsize.md)|Gibt die Größe in Bytes, der den Wert der Eigenschaft zurück.|  
|[GetReference](../../../extensibility/debugger/reference/idebugproperty2-getreference.md)|Gibt einen Verweis auf der Wert dieser Eigenschaft zurück.|  
|[GetExtendedInfo](../../../extensibility/debugger/reference/idebugproperty2-getextendedinfo.md)|Gibt den erweiterten Informationen einer Eigenschaft zurück.|  
  
## <a name="remarks"></a>Hinweise  
 Eine Eigenschaft, dargestellt durch ein `IDebugProperty2` Schnittstellen, kann als Wert mit einem Namen, einen Typ und eine Adresse betrachtet werden. Weitere allgemeine ausgedrückt ein `IDebugProperty2` darstellen kann, alle Elemente, die eine hierarchische Struktur, mit übergeordneten und untergeordneten Knoten besitzt.  
  
 Eine Eigenschaft ist in der Regel vorübergehend, z. B. nur so lange wie der aktuelle Stapelrahmen andauert. Andererseits, dargestellt durch einen Verweis ein [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md) Schnittstelle, so lange beibehalten, solange der Wert im Arbeitsspeicher bleibt.  
  
 Die IDE verwenden, kann die `IDebugProperty2` Schnittstelle, um Benutzer zu suchen und Ändern von Eigenschaften zur Laufzeit.  
  
## <a name="requirements"></a>Anforderungen  
 Header: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Siehe auch  
 [Wichtige Schnittstellen](../../../extensibility/debugger/reference/core-interfaces.md)   
 [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md)   
 [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)

