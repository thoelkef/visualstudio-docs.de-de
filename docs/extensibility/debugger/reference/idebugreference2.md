---
title: "IDebugReference2 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugReference2"
helpviewer_keywords: 
  - "IDebugReference2-Schnittstelle"
ms.assetid: 3cfed312-f532-4bce-84a5-1677c14567d7
caps.latest.revision: 11
caps.handback.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugReference2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Diese Schnittstelle stellt einen Verweis auf eine Stapelrahmen \- Eigenschaft oder einer anderen Eigenschaft dar.  
  
> [!NOTE]
>  `IDebugReference2` ist für eine zukünftige Verwendung reserviert und alle zugehörigen Methoden sollten `E_NOTIMPL`zurückgeben.  
  
## Syntax  
  
```  
IDebugReference2 : IUnknown  
```  
  
## Hinweise für Implementierer  
 DE implementiert diese Schnittstelle, um einen Verweis auf eine bestimmte Weise Wert darstellt.  Beispielsweise könnte der Wert eines numerischen Werts aufgrund einer Ausdrucksauswertung, einem Speicher, der für die Anzeige des Arbeitsspeichers verwendet wurden, oder eine Liste von Registern und deren Werte sein.  
  
## Hinweise für Aufrufer  
 [\[GetReference](../../../extensibility/debugger/reference/idebugproperty2-getreference.md) Aufruf zum Abrufen dieser Schnittstelle.  [GetParent](../../../extensibility/debugger/reference/idebugreference2-getparent.md) und [GetDerivedMostReference](../../../extensibility/debugger/reference/idebugreference2-getderivedmostreference.md) hinaus geben diese Schnittstelle zurück.  
  
## Methoden in die Vtable\-Reihenfolge  
 In der folgenden Tabelle werden die Methoden von `IDebugReference2`an.  
  
|Methode|Beschreibung|  
|-------------|------------------|  
|[GetReferenceInfo](../../../extensibility/debugger/reference/idebugreference2-getreferenceinfo.md)|Ruft die [DEBUG\_REFERENCE\_INFO](../../../extensibility/debugger/reference/debug-reference-info.md) Struktur ab, die diesen Verweis beschreibt.|  
|[SetValueAsString](../../../extensibility/debugger/reference/idebugreference2-setvalueasstring.md)|Legt den Wert dieses Verweises aus einer Zeichenfolge fest.|  
|[SetValueAsReference](../../../extensibility/debugger/reference/idebugreference2-setvalueasreference.md)|Legt den Wert dieses Verweises auf einen anderen Verweis fest.|  
|[EnumChildren](../../../extensibility/debugger/reference/idebugreference2-enumchildren.md)|Listet die untergeordneten Elemente dieses Verweises auf.|  
|[GetParent](../../../extensibility/debugger/reference/idebugreference2-getparent.md)|Ruft das übergeordnete Element dieses Verweises ab.|  
|[GetDerivedMostReference](../../../extensibility/debugger/reference/idebugreference2-getderivedmostreference.md)|Ruft den höchst\-abgeleiteten Verweis dieses Verweises ab.|  
|[GetMemoryBytes](../../../extensibility/debugger/reference/idebugreference2-getmemorybytes.md)|Ruft die Bytes an Arbeitsspeicher ab, auf den dieser Verweis verweist.|  
|[GetMemoryContext](../../../extensibility/debugger/reference/idebugreference2-getmemorycontext.md)|Ruft einen Speicher als Elementkontext dieser Referenz ab.|  
|[GetSize](../../../extensibility/debugger/reference/idebugreference2-getsize.md)|Ruft die Größe \(in Bytes\) des Verweises ab.|  
|[SetReferenceType](../../../extensibility/debugger/reference/idebugreference2-setreferencetype.md)|Legt den Referenztyp fest.|  
|[Vergleichen](../../../extensibility/debugger/reference/idebugreference2-compare.md)|Vergleicht diesen Verweis mit einem anderen.|  
  
## Hinweise  
  
> [!NOTE]
>  Dieser Verwendung von „Eigenschaft“ sollte nicht zu verwechseln mit dieser Bedeutung einer Membervariablen einer Klasse, obwohl `IDebugReference2` eine solche Entität darstellen kann.  
  
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) stellt eine Eigenschaft, während `IDebugReference2` einen Verweis auf eine Eigenschaft darstellt \(in der Regel ein Verweis auf ein Objekt im Programm, das gedebuggt wird.  
  
 Der Hauptunterschied zwischen einer Eigenschaft und einem Verweis ist, dass eine Eigenschaft einer benannten Instanz eines Objekts als Verweis auf eine unbenannte Instanz verweist.  Zum Beispiel kann eine Eigenschaft verweist auf ein Objekt im Heap des Programms durch `"a.b"`an.  Eine andere Eigenschaft verweist möglicherweise das gleiche Objekt wie `"c.d"`an.  Die Möglichkeit des erhöhen, auf dieser Eigenschaft erfordert dieses `"a.b"` , oder `"c.d"` ist im Bereich.  Ein Verweis auf dieses Objekt denselben namenlos ist. Es kann das verwiesen wird, sofern der Speicher für dieses Objekt gültig ist.  
  
 Eine `IDebugProperty2`\-Schnittstelle kann als Wert betrachtet werden mit einem Namen, einem Typ und einer angegebenen Adresse.  `IDebugReference2`kann für einen Typ und eine Adresse dagegen beibehalten werden.  
  
## Anforderungen  
 Header: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Siehe auch  
 [Core\-Schnittstellen](../../../extensibility/debugger/reference/core-interfaces.md)   
 [DEBUG\_REFERENCE\_INFO](../../../extensibility/debugger/reference/debug-reference-info.md)   
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)   
 [\[GetReference](../../../extensibility/debugger/reference/idebugproperty2-getreference.md)