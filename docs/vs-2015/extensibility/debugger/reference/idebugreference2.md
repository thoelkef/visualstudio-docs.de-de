---
title: IDebugReference2 | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugReference2
helpviewer_keywords:
- IDebugReference2 interface
ms.assetid: 3cfed312-f532-4bce-84a5-1677c14567d7
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: ac7e825bd33c184d580ada96843366f6d1627f22
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "90840882"
---
# <a name="idebugreference2"></a>IDebugReference2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Diese Schnittstelle stellt einen Verweis auf eine Stapel Rahmen Eigenschaft oder eine andere Eigenschaft dar.  
  
> [!NOTE]
> `IDebugReference2` ist für die zukünftige Verwendung reserviert, und alle zugehörigen Methoden sollten zurückgeben `E_NOTIMPL` .  
  
## <a name="syntax"></a>Syntax  
  
```  
IDebugReference2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Hinweise für Implementierer  
 Die de implementiert diese Schnittstelle, um einen Verweis auf eine bestimmte Art von Wert darzustellen. Der Wert kann z. b. ein numerischer Wert als Ergebnis einer Ausdrucks Auswertung, ein Speicher Kontext, der zum Anzeigen von Arbeitsspeicher verwendet wird, oder eine Liste von Registern und deren Werten sein.  
  
## <a name="notes-for-callers"></a>Hinweise für Aufrufer  
 Rufen Sie [getreferenzierung](../../../extensibility/debugger/reference/idebugproperty2-getreference.md) zum Abrufen dieser Schnittstelle auf. " [GetParent](../../../extensibility/debugger/reference/idebugreference2-getparent.md) " und " [getderivedmustreferenzierung](../../../extensibility/debugger/reference/idebugreference2-getderivedmostreference.md) " geben ebenfalls diese Schnittstelle zurück.  
  
## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge  
 In der folgenden Tabelle sind die Methoden von aufgeführt `IDebugReference2` .  
  
|Methode|BESCHREIBUNG|  
|------------|-----------------|  
|[GetReferenceInfo](../../../extensibility/debugger/reference/idebugreference2-getreferenceinfo.md)|Ruft die [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md) -Struktur ab, die diesen Verweis beschreibt.|  
|[SetValueAsString](../../../extensibility/debugger/reference/idebugreference2-setvalueasstring.md)|Legt den Wert dieses Verweises aus einer Zeichenfolge fest.|  
|[SetValueAsReference](../../../extensibility/debugger/reference/idebugreference2-setvalueasreference.md)|Legt den Wert dieses Verweises aus einem anderen Verweis fest.|  
|[EnumChildren](../../../extensibility/debugger/reference/idebugreference2-enumchildren.md)|Listet die untergeordneten Elemente dieses Verweises auf.|  
|[GetParent](../../../extensibility/debugger/reference/idebugreference2-getparent.md)|Ruft das übergeordnete Element dieses Verweises ab.|  
|[GetDerivedMostReference](../../../extensibility/debugger/reference/idebugreference2-getderivedmostreference.md)|Ruft den am weitesten abgeleiteten Verweis dieses Verweises ab.|  
|[GetMemoryBytes](../../../extensibility/debugger/reference/idebugreference2-getmemorybytes.md)|Ruft die Arbeitsspeicher Bytes ab, auf die sich dieser Verweis bezieht.|  
|[GetMemoryContext](../../../extensibility/debugger/reference/idebugreference2-getmemorycontext.md)|Ruft einen Speicher Kontext für diesen Verweis ab.|  
|[GetSize](../../../extensibility/debugger/reference/idebugreference2-getsize.md)|Ruft die Größe dieses Verweises in Bytes ab.|  
|[SetReferenceType](../../../extensibility/debugger/reference/idebugreference2-setreferencetype.md)|Legt diesen Verweistyp fest.|  
|[Vergleichen](../../../extensibility/debugger/reference/idebugreference2-compare.md)|Vergleicht diesen Verweis mit einem anderen.|  
  
## <a name="remarks"></a>Bemerkungen  
  
> [!NOTE]
> Diese Verwendung von "Property" sollte nicht mit der Bedeutung einer Element Variablen einer Klasse verwechselt werden, obwohl eine `IDebugReference2` solche Entität darstellen kann.  
  
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) stellt eine Eigenschaft dar, während `IDebugReference2` einen Verweis auf eine Eigenschaft darstellt, in der Regel ein Verweis auf ein Objekt in dem Programm, das deentschlgt wird.  
  
 Der Hauptunterschied zwischen einer Eigenschaft und einem Verweis besteht darin, dass eine Eigenschaft auf eine benannte Instanz eines Objekts verweist, während ein Verweis auf eine unbenannte Instanz verweist. Eine Eigenschaft kann z. b. auf ein Objekt im Heap des Programms durch verweisen `"a.b"` . Eine andere Eigenschaft verweist möglicherweise auf dasselbe Objekt wie `"c.d"` . Die Möglichkeit, auf diese Eigenschaft zu verweisen, erfordert, dass `"a.b"` oder im Gültigkeits `"c.d"` Bereich liegen. Ein Verweis auf dieses Objekt ist namenenlos. auf das-Objekt kann verwiesen werden, solange der Arbeitsspeicher für dieses Objekt gültig ist.  
  
 Eine `IDebugProperty2` Schnittstelle kann als Wert mit einem Namen, einem Typ und einer Adresse betrachtet werden. Eine `IDebugReference2` kann andererseits als Typ und als Adresse betrachtet werden.  
  
## <a name="requirements"></a>Anforderungen  
 Header: msdbg. h  
  
 Namespace: Microsoft. VisualStudio. Debugger. Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Weitere Informationen  
 [Kern Schnittstellen](../../../extensibility/debugger/reference/core-interfaces.md)   
 [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md)   
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)   
 [GetReference](../../../extensibility/debugger/reference/idebugproperty2-getreference.md)
