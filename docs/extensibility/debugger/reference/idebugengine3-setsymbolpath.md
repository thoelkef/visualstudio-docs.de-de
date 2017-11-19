---
title: IDebugEngine3::SetSymbolPath | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugEngine3::SetSymbolPath
helpviewer_keywords: IDebugEngine3::SetSymbolPath
ms.assetid: 47b48f84-8a96-401f-84df-0baa8a96d26e
caps.latest.revision: "12"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 77a5f294acf60eebc745cb78042e0ea3431fc998
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="idebugengine3setsymbolpath"></a>IDebugEngine3::SetSymbolPath
Legt den Pfad oder die Pfade, die für die Debugsymbole durchsucht werden.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
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
 Die Zeichenfolge `szSymbolSearchPath` ist eine Liste von Pfaden für eine oder mehrere, durch Semikolons getrennt ein, nach Symbolen sucht. Diese Pfade können einen lokalen Pfad, einen Pfad im UNC-Format oder eine URL sein. Diese Pfade können auch eine Mischung aus verschiedenen Typen sein. Wenn der Pfad UNC ist (z. B. \\\Symserver\Symbols), und klicken Sie dann das Debugmodul bestimmt werden soll, wenn der Pfad auf einen anderen Symbolserver und sollte in der Lage, laden Sie Symbole von diesem Server, die im angegebenen Pfad zwischenzuspeichern `szSymbolCachePath`.  
  
 Der Symbolpfad kann auch eine oder mehrere Cache Speicherorte enthalten. Caches in Reihenfolge ihrer Priorität, mit der höchsten Priorität Cache zuerst aufgeführt sind und ein senkrechter * Symbole. Zum Beispiel:  
  
```  
\\symbols\symbols;\\someotherserver\symbols;c:\symbols\httpsymbols*http://msdl.microsoft.com  
```  
  
 Die [LoadSymbols](../../../extensibility/debugger/reference/idebugengine3-loadsymbols.md) -Methode führt die tatsächliche Last der Symbole.  
  
## <a name="see-also"></a>Siehe auch  
 [LoadSymbols](../../../extensibility/debugger/reference/idebugengine3-loadsymbols.md)   
 [IDebugEngine3](../../../extensibility/debugger/reference/idebugengine3.md)