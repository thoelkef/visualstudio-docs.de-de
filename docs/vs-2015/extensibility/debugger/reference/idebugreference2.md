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
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63438970"
---
# <a name="idebugreference2"></a>IDebugReference2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Diese Schnittstelle stellt einen Verweis auf eine Stack-Frame-Eigenschaft oder eine andere Eigenschaft dar.  
  
> [!NOTE]
> `IDebugReference2` ist reserviert für zukünftige Verwendung und alle seine Methoden sollten zurückgeben `E_NOTIMPL`.  
  
## <a name="syntax"></a>Syntax  
  
```  
IDebugReference2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Hinweise für Implementierer  
 Die DE implementiert diese Schnittstelle, um einen Verweis auf eine bestimmte Art von Wert darstellen. Der Wert kann z. B. einen numerischen Wert als Ergebnis der Auswertung eines Ausdrucks, einen Speicherkontext, der zum Anzeigen von Arbeitsspeicher oder eine Liste der Register und deren Werte sein.  
  
## <a name="notes-for-callers"></a>Hinweise für Aufrufer  
 Rufen Sie [GetReference](../../../extensibility/debugger/reference/idebugproperty2-getreference.md) dieser Schnittstelle abgerufen. [GetParent](../../../extensibility/debugger/reference/idebugreference2-getparent.md) und [GetDerivedMostReference](../../../extensibility/debugger/reference/idebugreference2-getderivedmostreference.md) diese Schnittstelle auch zurückgeben.  
  
## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge  
 Die folgende Tabelle zeigt die Methoden der `IDebugReference2`.  
  
|Methode|Beschreibung|  
|------------|-----------------|  
|[GetReferenceInfo](../../../extensibility/debugger/reference/idebugreference2-getreferenceinfo.md)|Ruft die [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md) Struktur, die dieser Verweis beschreibt.|  
|[SetValueAsString](../../../extensibility/debugger/reference/idebugreference2-setvalueasstring.md)|Legt den Wert des Verweises aus einer Zeichenfolge.|  
|[SetValueAsReference](../../../extensibility/debugger/reference/idebugreference2-setvalueasreference.md)|Legt den Wert des Verweises von einem anderen Verweis.|  
|[EnumChildren](../../../extensibility/debugger/reference/idebugreference2-enumchildren.md)|Listet die untergeordneten Elemente des Verweises an.|  
|[GetParent](../../../extensibility/debugger/reference/idebugreference2-getparent.md)|Ruft das übergeordnete Element des Verweises ab.|  
|[GetDerivedMostReference](../../../extensibility/debugger/reference/idebugreference2-getderivedmostreference.md)|Ruft den am stärksten abgeleiteten Verweis des Verweises ab.|  
|[GetMemoryBytes](../../../extensibility/debugger/reference/idebugreference2-getmemorybytes.md)|Ruft ab, die Arbeitsspeicherbytes, die sich dieser Verweis bezieht.|  
|[GetMemoryContext](../../../extensibility/debugger/reference/idebugreference2-getmemorycontext.md)|Ruft einen Speicherkontext für diesen Verweis ab.|  
|[GetSize](../../../extensibility/debugger/reference/idebugreference2-getsize.md)|Ruft die Größe in Bytes des Verweises an.|  
|[SetReferenceType](../../../extensibility/debugger/reference/idebugreference2-setreferencetype.md)|Legt den Verweistyp fest.|  
|[Compare](../../../extensibility/debugger/reference/idebugreference2-compare.md)|Vergleicht diesen Verweis mit einem anderen.|  
  
## <a name="remarks"></a>Hinweise  
  
> [!NOTE]
> Diese Verwendung von "Property" dürfen nicht verwechselt werden mit, d. h. einer Membervariablen einer Klasse, obwohl ein `IDebugReference2` können solche Entität darstellen.  
  
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) stellt eine Eigenschaft, während `IDebugReference2` stellt einen Verweis auf eine Eigenschaft, die in der Regel einen Verweis auf ein Objekt in das derzeit debuggte Programm dar.  
  
 Der Hauptunterschied zwischen einer Eigenschaft und einen Verweis besteht darin, dass eine Eigenschaft mit einer benannten Instanz eines Objekts bezieht, während ein Verweis auf eine unbenannte Instanz bezieht. Z. B. eine Eigenschaft bezieht sich möglicherweise auf ein Objekt in den Heapspeicher des Programms durch `"a.b"`. Eine andere Eigenschaft bezieht sich möglicherweise auf dasselbe Objekt wie `"c.d"`. Die Methode zum Verweisen auf diese Eigenschaft erfordert, dass `"a.b"` oder `"c.d"` werden im Bereich. Ein Verweis auf das gleiche Objekt ist namenlosen; das Objekt kann zum verwiesen werden, solange der Arbeitsspeicher für das Objekt gültig ist.  
  
 Ein `IDebugProperty2` Schnittstelle kann als Wert mit einem Namen, einen Typ und eine Adresse betrachtet werden. Ein `IDebugReference2`, auf dem anderen übergeben, können als ein Typ und eine Adresse betrachtet werden.  
  
## <a name="requirements"></a>Anforderungen  
 Header: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Siehe auch  
 [Wichtige Schnittstellen](../../../extensibility/debugger/reference/core-interfaces.md)   
 [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md)   
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)   
 [GetReference](../../../extensibility/debugger/reference/idebugproperty2-getreference.md)
