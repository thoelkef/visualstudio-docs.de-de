---
title: IDebugEngine3::SetSymbolPath | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugEngine3::SetSymbolPath
helpviewer_keywords:
- IDebugEngine3::SetSymbolPath
ms.assetid: 47b48f84-8a96-401f-84df-0baa8a96d26e
caps.latest.revision: 13
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: f74fafc325693df6a312647c9e9060a24cf256ef
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49863554"
---
# <a name="idebugengine3setsymbolpath"></a>IDebugEngine3::SetSymbolPath
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Legt fest, den Pfad oder die Pfade, die für das Debuggen von Symbolen durchsucht werden.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
HRESULT SetSymbolPath (  
   LPOLESTR            szSymbolSearchPath,  
   LPOLESTR            szSymbolCachePath,  
   LOAD_SYMBOLS_FLAGS  Flags  
);  
```  
  
```csharp  
int SetSymbolPath(  
   string                    szSymbolSearchPath,   
   string                    szSymbolCachePath,   
   enum_LOAD_SYMBOLS_FLAGS   Flags  
);  
```  
  
#### <a name="parameters"></a>Parameter  
  
|Parameter|Beschreibung|  
|---------------|-----------------|  
|`szSymbolSearchPath`|[in] Eine Zeichenfolge mit den Symbolsuchpfad oder die Pfade. Einzelheiten finden Sie unter "Hinweise". Darf nicht NULL sein.|  
|`szSymbolCachePath`|[in] Eine Zeichenfolge mit den lokalen Pfad, in dem Symbole zwischengespeichert werden können. Darf nicht NULL sein.|  
|`Flags`|[in] Nicht verwendet. immer auf 0 festgelegt.|  
  
## <a name="return-value"></a>Rückgabewert  
 Im Erfolgsfall gibt S_OK zurück. Andernfalls wird ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Hinweise  
 Die Zeichenfolge `szSymbolSearchPath` ist eine Liste von einem oder mehreren Pfaden, getrennt durch ein Semikolon nach Symbolen sucht. Diese Pfade können es sich um einen lokalen Pfad, einen UNC-Format-Pfad oder eine URL sein. Diese Pfade können auch eine Mischung verschiedener Domänentypen sein. Wenn der Pfad UNC ist (z. B. \\\Symserver\Symbols), und klicken Sie dann die Debug-Engine bestimmt werden soll, wenn der Pfad auf einem Symbolserver und sollte in der Lage, laden Symbole von diesem Server, und speichern Sie sie in der Pfadangabe von `szSymbolCachePath`.  
  
 Der Symbolpfad kann auch eine oder mehrere cachespeicherorte enthalten. Caches sind in der Reihenfolge ihrer Priorität, mit der höchsten Priorität Cache zuerst aufgeführt und getrennt von * Symbole. Zum Beispiel:  
  
```  
\\symbols\symbols;\\someotherserver\symbols;c:\symbols\httpsymbols*http://msdl.microsoft.com  
```  
  
 Die [LoadSymbols](../../../extensibility/debugger/reference/idebugengine3-loadsymbols.md) Methode führt die tatsächliche Last der Symbole.  
  
## <a name="see-also"></a>Siehe auch  
 [LoadSymbols](../../../extensibility/debugger/reference/idebugengine3-loadsymbols.md)   
 [IDebugEngine3](../../../extensibility/debugger/reference/idebugengine3.md)

