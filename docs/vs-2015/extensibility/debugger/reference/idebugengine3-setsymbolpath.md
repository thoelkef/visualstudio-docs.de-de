---
title: 'IDebugEngine3:: setsymbolpath | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugEngine3::SetSymbolPath
helpviewer_keywords:
- IDebugEngine3::SetSymbolPath
ms.assetid: 47b48f84-8a96-401f-84df-0baa8a96d26e
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: d3ea3086931ab655209a5ca26d4d1527462fb205
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "77476799"
---
# <a name="idebugengine3setsymbolpath"></a>IDebugEngine3::SetSymbolPath
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Legt den Pfad oder die Pfade fest, die nach Debugsymbolen durchsucht werden.  
  
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
  
|Parameter|BESCHREIBUNG|  
|---------------|-----------------|  
|`szSymbolSearchPath`|in Zeichenfolge, die den Pfad oder die Pfade der Symbol Suche enthält. Weitere Informationen finden Sie unter "Hinweise". Darf nicht NULL sein.|  
|`szSymbolCachePath`|in Zeichenfolge, die den lokalen Pfad enthält, in dem Symbole zwischengespeichert werden können Darf nicht NULL sein.|  
|`Flags`|in Nicht verwendet; immer auf 0 festgelegt.|  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird S_OK zurückgegeben. Andernfalls wird ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Bemerkungen  
 Die Zeichenfolge `szSymbolSearchPath` ist eine Liste mit einem oder mehreren durch Semikolons getrennten Pfaden, um nach Symbolen zu suchen. Diese Pfade können ein lokaler Pfad, ein UNC-Pfad oder eine URL sein. Diese Pfade können auch eine Mischung verschiedener Typen sein. Wenn der Pfad UNC ist (z. \\ b. \symserver\symbols), sollte die Debug-Engine ermitteln, ob der Pfad zu einem Symbol Server gehört, und dass Sie in der Lage sein soll, Symbole von diesem Server zu laden und Sie in dem von angegebenen Pfad zwischenzuspeichern `szSymbolCachePath` .  
  
 Der Symbol Pfad kann auch einen oder mehrere Cache Speicherorte enthalten. Caches werden in der Prioritäts Reihenfolge aufgelistet, wobei der Cache mit der höchsten Priorität zuerst und durch * Symbole getrennt ist. Beispiel:  
  
```  
\\symbols\symbols;\\someotherserver\symbols;c:\symbols\httpsymbols*https://msdl.microsoft.com  
```  
  
 Die [loadsymbols](../../../extensibility/debugger/reference/idebugengine3-loadsymbols.md) -Methode führt die tatsächliche Auslastung der Symbole aus.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Loadsymbols](../../../extensibility/debugger/reference/idebugengine3-loadsymbols.md)   
 [IDebugEngine3](../../../extensibility/debugger/reference/idebugengine3.md)
