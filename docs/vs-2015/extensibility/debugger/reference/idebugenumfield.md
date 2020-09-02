---
title: Idebugenenfield | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugEnumField
helpviewer_keywords:
- IDebugEnumField interface
ms.assetid: 42f685bf-0f39-47f4-98b0-6022efe2bf97
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: ac993e3a4676f1c84a193ddbf6e9a3b5bc8fa235
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "65676505"
---
# <a name="idebugenumfield"></a>IDebugEnumField
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Diese Schnittstelle stellt einen Enumerationstyp dar.  
  
## <a name="syntax"></a>Syntax  
  
```  
IDebugEnumField : IDebugContainerField  
```  
  
## <a name="notes-for-implementers"></a>Hinweise für Implementierer  
 Ein Symbol Anbieter implementiert diese Schnittstelle, um eine Enumeration darzustellen.  
  
## <a name="notes-for-callers"></a>Hinweise für Aufrufer  
 Verwenden Sie [QueryInterface](https://msdn.microsoft.com/library/62fce95e-aafa-4187-b50b-e6611b74c3b3) , um diese Schnittstelle von der [idebugfield](../../../extensibility/debugger/reference/idebugfield.md) -Schnittstelle abzurufen, wenn [getkind](../../../extensibility/debugger/reference/idebugfield-getkind.md) zurückgibt `FIELD_TYPE_ENUM` .  
  
## <a name="methods-in-vtable-order"></a>Methoden in der Vtable-Reihenfolge  
 Zusätzlich zu den Methoden der `IDebugField` -Schnittstelle und der- `IDebugContainerField` Schnittstelle implementiert diese Schnittstelle die folgenden Methoden:  
  
|Methode|BESCHREIBUNG|  
|------------|-----------------|  
|[GetUnderlyingSymbol](../../../extensibility/debugger/reference/idebugenumfield-getunderlyingsymbol.md)|Gibt ein [idebugfeld](../../../extensibility/debugger/reference/idebugfield.md) zurück, das den Namen für diesen Enumerationstyp beschreibt.|  
|[GetStringFromValue](../../../extensibility/debugger/reference/idebugenumfield-getstringfromvalue.md)|Gibt den Namen der Enumerationskonstante zurück, die dem angegebenen Wert zugeordnet ist.|  
|[GetValueFromString](../../../extensibility/debugger/reference/idebugenumfield-getvaluefromstring.md)|Gibt den Wert zurück, der dem angegebenen enumerationskonstantennamen zugeordnet ist|  
|[GetValueFromStringCaseInsensitive](../../../extensibility/debugger/reference/idebugenumfield-getvaluefromstringcaseinsensitive.md)|Gibt den Wert zurück, der dem angegebenen Namen der Enumerationskonstante zugeordnet ist|  
  
## <a name="remarks"></a>Bemerkungen  
 Dabei handelt es sich um das zugrunde liegende Symbol, das tatsächlich an einen Speicherort mit [Bind](../../../extensibility/debugger/reference/idebugbinder-bind.md)gebunden ist.  
  
## <a name="requirements"></a>Requirements (Anforderungen)  
 Header: sh. h  
  
 Namespace: Microsoft. VisualStudio. Debugger. Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Weitere Informationen  
 [Symbol Anbieter Schnittstellen](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)   
 [Idebugcontainerfield](../../../extensibility/debugger/reference/idebugcontainerfield.md)   
 [Idebugfield](../../../extensibility/debugger/reference/idebugfield.md)   
 [Zwick](../../../extensibility/debugger/reference/idebugbinder-bind.md)
