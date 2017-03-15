---
title: "IDebugField | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugField"
helpviewer_keywords: 
  - "IDebugField-Schnittstelle"
ms.assetid: adecdd1c-b1b9-4027-92da-74cbe910636f
caps.latest.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 12
---
# IDebugField
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Diese Schnittstelle stellt eine Beschreibung. h. ein Feld eines Symbols oder des Typs dar.  
  
## Syntax  
  
```  
IDebugField : IUnknown  
```  
  
## Hinweise für Implementierer  
 Ein Symbol Anbieter implementiert diese Schnittstelle als Basisklasse für alle Felder.  
  
## Hinweise für Aufrufer  
 Diese Schnittstelle ist die Basisklasse für alle Felder.  Basierend auf den Rückgabewert aus [GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md), gibt diese Schnittstelle möglicherweise mehrere spezialisierte Schnittstellen zurück, indem [QueryInterface](/visual-cpp/atl/queryinterface)verwendet.  Darüber hinaus geben eine große Anzahl von Schnittstellen `IDebugField`\-Objekte aus verschiedenen Methoden zurück.  
  
## Methoden in die Vtable\-Reihenfolge  
 In der folgenden Tabelle werden die Methoden von `IDebugField`an.  
  
|Methode|Beschreibung|  
|-------------|------------------|  
|[GetInfo](../../../extensibility/debugger/reference/idebugfield-getinfo.md)|Ruft die anzeigbare Informationen über das Symbol oder den Typ ab.|  
|[GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md)|Ruft die Art des Felds ab.|  
|[GetType](../../../extensibility/debugger/reference/idebugfield-gettype.md)|Ruft den Typ des Felds ab.|  
|[GetContainer](../../../extensibility/debugger/reference/idebugfield-getcontainer.md)|Ruft den Container des Felds ab.|  
|[GetAddress](../../../extensibility/debugger/reference/idebugfield-getaddress.md)|Ruft die Adresse des Felds ab.|  
|[GetSize](../../../extensibility/debugger/reference/idebugfield-getsize.md)|Ruft die Größe des Felds in Bytes ab.|  
|[GetExtendedInfo](../../../extensibility/debugger/reference/idebugfield-getextendedinfo.md)|Ruft die erweiterten Informationen über ein Feld.|  
|[Gleich](../../../extensibility/debugger/reference/idebugfield-equal.md)|Vergleicht zwei Felder.|  
|[GetTypeInfo](../../../extensibility/debugger/reference/idebugfield-gettypeinfo.md)|Ruft TYPE\-unabhängige Informationen über das Symbol oder den Typ ab.|  
  
## Hinweise  
 Ein Typ ist mit Wechselstrom\-Sprache `typedef`.  
  
 Im folgenden Beispiel wird `weather` C\+\+ einen Klassentyp, und `sunny` und `stormy` Symbole sind:  
  
```cpp#  
class weather;  
weather sunny;  
weather stormy;  
```  
  
 Ob ein Feld darstellt, kann ein Symbol oder ein Typ bestimmt werden, indem [GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md) aufruft und das [FIELD\_KIND](../../../extensibility/debugger/reference/field-kind.md) Ergebnis überprüft.  Wenn das `FIELD_KIND_TYPE` Bit festgelegt wurde, ist das Feld ein Typ, und wenn das `FIELD_KIND_SYMBOL` Bit festgelegt ist, ist dies ein Symbol.  
  
## Anforderungen  
 Header: sh.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Siehe auch  
 [Symbol\-Provider\-Schnittstellen](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)