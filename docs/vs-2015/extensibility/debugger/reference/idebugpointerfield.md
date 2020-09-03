---
title: Idebugpointerfield | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugPointerField
helpviewer_keywords:
- IDebugPointerField interface
ms.assetid: d51bd5b2-f18e-4e27-b4fb-e6f652fbf635
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 9d92b1b4d6efda1b8f05c594368a05bd833c9f34
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "65705829"
---
# <a name="idebugpointerfield"></a>IDebugPointerField
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Diese Schnittstelle stellt einen Zeigertyp dar.  
  
## <a name="syntax"></a>Syntax  
  
```  
IDebugPointerField : IDebugContainerField  
```  
  
## <a name="notes-for-implementers"></a>Hinweise für Implementierer  
 Der Symbol Anbieter implementiert diese Schnittstelle, um einen Zeiger darzustellen.  
  
## <a name="notes-for-callers"></a>Hinweise für Aufrufer  
 Verwenden Sie [QueryInterface](https://msdn.microsoft.com/library/62fce95e-aafa-4187-b50b-e6611b74c3b3) , um diese Schnittstelle von der [idebugfield](../../../extensibility/debugger/reference/idebugfield.md) -Schnittstelle abzurufen, wenn [getkind](../../../extensibility/debugger/reference/idebugfield-getkind.md) zurückgibt `FIELD_TYPE_POINTER` .  
  
## <a name="methods-in-vtable-order"></a>Methoden in der Vtable-Reihenfolge  
 Zusätzlich zu den Methoden der `IDebugField` -Schnittstelle und der- `IDebugContainerField` Schnittstelle implementiert diese Schnittstelle die folgende Methode:  
  
|Methode|BESCHREIBUNG|  
|------------|-----------------|  
|[GetDereferencedField](../../../extensibility/debugger/reference/idebugpointerfield-getdereferencedfield.md)|Gibt ein [idebugfeld](../../../extensibility/debugger/reference/idebugfield.md) zurück, das das Ziel des Zeigers beschreibt.|  
  
## <a name="remarks"></a>Bemerkungen  
 In C/C++ kann ein Zeiger ein Container sein, wenn er mit der Array Notation verwendet wird. Hat z. b `char *pString` `pString` . einen Typ von Zeiger auf `char` . `pString[3]` weist den Typ eines Containers auf, bei dem es sich um einen Zeiger auf handelt, der auf `char` das vierte Element dieses Containers verweist.  
  
## <a name="requirements"></a>Requirements (Anforderungen)  
 Header: sh. h  
  
 Namespace: Microsoft. VisualStudio. Debugger. Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Weitere Informationen  
 [Symbol Anbieter Schnittstellen](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)   
 [Idebugfield](../../../extensibility/debugger/reference/idebugfield.md)   
 [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md)
