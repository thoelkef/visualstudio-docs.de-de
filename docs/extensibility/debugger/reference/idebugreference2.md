---
title: IDebugReference2 | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugReference2
helpviewer_keywords: IDebugReference2 interface
ms.assetid: 3cfed312-f532-4bce-84a5-1677c14567d7
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 30f3b8351789adbb52651909cf9ff3b669934d66
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="idebugreference2"></a>IDebugReference2
Diese Schnittstelle stellt einen Verweis auf eine Stack-Frame-Eigenschaft oder eine andere Eigenschaft dar.  
  
> [!NOTE]
>  `IDebugReference2`ist reserviert für zukünftige Verwendung, und alle seine Methoden zurückgeben sollte `E_NOTIMPL`.  
  
## <a name="syntax"></a>Syntax  
  
```  
IDebugReference2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Hinweise für Implementierer  
 Die DE implementiert diese Schnittstelle, um einen Verweis auf eine bestimmte Art von Wert darstellen. Der Wert kann z. B. einen numerischen Wert als Ergebnis eine Auswertung von Ausdrücken, eine Speicherkontext zum Anzeigen von Arbeitsspeicher oder eine Liste von Registern und deren Werten sein.  
  
## <a name="notes-for-callers"></a>Hinweise für Aufrufer  
 Rufen Sie [GetReference](../../../extensibility/debugger/reference/idebugproperty2-getreference.md) beim Abrufen dieser Schnittstelle. [GetParent](../../../extensibility/debugger/reference/idebugreference2-getparent.md) und [GetDerivedMostReference](../../../extensibility/debugger/reference/idebugreference2-getderivedmostreference.md) diese Schnittstelle auch zurück.  
  
## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge  
 Die folgende Tabelle zeigt die Methoden der `IDebugReference2`.  
  
|Methode|Beschreibung|  
|------------|-----------------|  
|[GetReferenceInfo](../../../extensibility/debugger/reference/idebugreference2-getreferenceinfo.md)|Ruft die [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md) Struktur, die dieser Verweis beschreibt.|  
|[SetValueAsString](../../../extensibility/debugger/reference/idebugreference2-setvalueasstring.md)|Legt den Wert des Verweises aus einer Zeichenfolge.|  
|[SetValueAsReference](../../../extensibility/debugger/reference/idebugreference2-setvalueasreference.md)|Legt den Wert des Verweises aus eines anderen Verweises.|  
|[EnumChildren](../../../extensibility/debugger/reference/idebugreference2-enumchildren.md)|Listet die untergeordneten Elemente des Verweises an.|  
|[GetParent](../../../extensibility/debugger/reference/idebugreference2-getparent.md)|Ruft das übergeordnete Element des Verweises ab.|  
|[GetDerivedMostReference](../../../extensibility/debugger/reference/idebugreference2-getderivedmostreference.md)|Ruft die am meisten abgeleiteten Verweis des Verweises ab.|  
|[GetMemoryBytes](../../../extensibility/debugger/reference/idebugreference2-getmemorybytes.md)|Ruft die Speicherbytes an, zu denen diese Referenz bezieht sich, ab.|  
|[GetMemoryContext](../../../extensibility/debugger/reference/idebugreference2-getmemorycontext.md)|Ruft eine Arbeitsspeicher-Kontext für diesen Verweis ab.|  
|[GetSize](../../../extensibility/debugger/reference/idebugreference2-getsize.md)|Ruft die Größe in Bytes des Verweises an.|  
|[SetReferenceType](../../../extensibility/debugger/reference/idebugreference2-setreferencetype.md)|Legt den Verweistyp fest.|  
|[Compare](../../../extensibility/debugger/reference/idebugreference2-compare.md)|Vergleicht diesen Verweis mit einem anderen.|  
  
## <a name="remarks"></a>Hinweise  
  
> [!NOTE]
>  Diese Verwendung von "Property" dürfen nicht mit, d. h. einer Klasse, einer Membervariable verwechselt werden, obwohl ein `IDebugReference2` können solche Entität darstellen.  
  
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) stellt eine Eigenschaft während `IDebugReference2` einen Verweis auf eine Eigenschaft, die in der Regel einen Verweis auf ein Objekt im zu debuggenden Programms darstellt.  
  
 Der Hauptunterschied zwischen einer Eigenschaft und einem Verweis ist, dass eine Eigenschaft mit einer benannten Instanz eines Objekts bezieht, während ein Verweis auf eine unbenannte Instanz verweist. Beispielsweise kann eine Eigenschaft verweisen, auf ein Objekt in das Programm Heap durch `"a.b"`. Eine andere Eigenschaft kann sich auf das gleiche Objekt wie beziehen `"c.d"`. Die Methode zum Verweisen auf diese Eigenschaft erfordert, dass `"a.b"` oder `"c.d"` im Bereich liegen. Ein Verweis auf das gleiche Objekt ist namenlos; das Objekt kann verwiesen werden, solange der Arbeitsspeicher für dieses Objekt gültig ist.  
  
 Ein `IDebugProperty2` Schnittstelle als einen Wert mit einem Namen, einen Typ und eine Adresse betrachtet werden kann. Ein `IDebugReference2`, auf dem anderen andererseits, können als einen Typ und eine Adresse betrachtet werden.  
  
## <a name="requirements"></a>Anforderungen  
 Header: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Siehe auch  
 [Core-Schnittstellen](../../../extensibility/debugger/reference/core-interfaces.md)   
 [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md)   
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)   
 [GetReference](../../../extensibility/debugger/reference/idebugproperty2-getreference.md)