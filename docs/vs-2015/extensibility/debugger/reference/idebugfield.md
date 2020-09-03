---
title: Idebugfield | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugField
helpviewer_keywords:
- IDebugField interface
ms.assetid: adecdd1c-b1b9-4027-92da-74cbe910636f
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 8bc18204d3cbe20635ab0680a50b4d1555dce2ce
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "65690305"
---
# <a name="idebugfield"></a>IDebugField
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Diese Schnittstelle stellt ein Feld dar, d. h. eine Beschreibung eines Symbols oder Typs.  
  
## <a name="syntax"></a>Syntax  
  
```  
IDebugField : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Hinweise für Implementierer  
 Ein Symbol Anbieter implementiert diese Schnittstelle als Basisklasse für alle Felder.  
  
## <a name="notes-for-callers"></a>Hinweise für Aufrufer  
 Diese Schnittstelle ist die Basisklasse für alle Felder. Basierend auf dem Rückgabewert von [getkind](../../../extensibility/debugger/reference/idebugfield-getkind.md)kann diese Schnittstelle mithilfe von [QueryInterface](https://msdn.microsoft.com/library/62fce95e-aafa-4187-b50b-e6611b74c3b3)weitere spezialisierte Schnittstellen zurückgeben. Außerdem geben viele Schnittstellen `IDebugField` Objekte aus verschiedenen Methoden zurück.  
  
## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge  
 In der folgenden Tabelle sind die Methoden von aufgeführt `IDebugField` .  
  
|Methode|BESCHREIBUNG|  
|------------|-----------------|  
|[GetInfo](../../../extensibility/debugger/reference/idebugfield-getinfo.md)|Ruft Informationen über das Symbol oder den Typ ab.|  
|[GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md)|Ruft die Art des Felds ab.|  
|[GetType](../../../extensibility/debugger/reference/idebugfield-gettype.md)|Ruft den Typ des Felds ab.|  
|[GetContainer](../../../extensibility/debugger/reference/idebugfield-getcontainer.md)|Ruft den Container des Felds ab.|  
|[GetAddress](../../../extensibility/debugger/reference/idebugfield-getaddress.md)|Ruft die Adresse des Felds ab.|  
|[GetSize](../../../extensibility/debugger/reference/idebugfield-getsize.md)|Ruft die Größe eines Felds in Bytes ab.|  
|[GetExtendedInfo](../../../extensibility/debugger/reference/idebugfield-getextendedinfo.md)|Ruft erweiterte Informationen zu einem Feld ab.|  
|[Gleich](../../../extensibility/debugger/reference/idebugfield-equal.md)|Vergleicht zwei Felder.|  
|[GetTypeInfo](../../../extensibility/debugger/reference/idebugfield-gettypeinfo.md)|Ruft typunabhängige Informationen über das Symbol oder den Typ ab.|  
  
## <a name="remarks"></a>Bemerkungen  
 Ein Typ entspricht der Programmiersprache C `typedef` .  
  
 Im folgenden Beispiel für die C++-Sprache `weather` ist ein Klassentyp, und `sunny` und `stormy` sind Symbole:  
  
```cpp#  
class weather;  
weather sunny;  
weather stormy;  
```  
  
 Gibt an, ob ein Feld ein Symbol oder einen Typ darstellt, indem [getkind](../../../extensibility/debugger/reference/idebugfield-getkind.md) aufgerufen und das [FIELD_KIND](../../../extensibility/debugger/reference/field-kind.md) Ergebnis überprüft wird. Wenn das- `FIELD_KIND_TYPE` Bit festgelegt ist, ist das Feld ein-Typ, und wenn das- `FIELD_KIND_SYMBOL` Bit festgelegt ist, ist es ein Symbol.  
  
## <a name="requirements"></a>Requirements (Anforderungen)  
 Header: sh. h  
  
 Namespace: Microsoft. VisualStudio. Debugger. Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Weitere Informationen  
 [Symbol Provider Interfaces](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)
