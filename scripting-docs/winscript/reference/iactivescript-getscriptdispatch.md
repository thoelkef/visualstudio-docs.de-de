---
title: 'IActiveScript:: getscriptdispatch | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScript.GetScriptDispatch
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScript_GetScriptDispatch
ms.assetid: 2092ccd4-1f4c-493a-b5b7-077a70ce95ca
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ba53f2eccde18bd5b2d9c609ea680b50cb7261c9
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575758"
---
# <a name="iactivescriptgetscriptdispatch"></a>IActiveScript::GetScriptDispatch
Ruft die `IDispatch`-Schnittstelle für die Methoden und Eigenschaften ab, die dem aktuell laufenden Skript zugeordnet sind.  
  
## <a name="syntax"></a>Syntax  
  
```cpp
HRESULT GetScriptDispatch(  
    LPCOLESTR pstrItemName  // address of item name  
    IDispatch **ppdisp      // receives IDispatch pointer  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pstrItemName`  
 in Die Adresse eines Puffers, der den Namen des Elements enthält, für das der Aufrufer das zugeordnete dispatchobjekt benötigt. Wenn dieser Parameter `NULL` ist, enthält das dispatchobjekt alle globalen Methoden und Eigenschaften, die vom Skript definiert werden, als Member. Durch die `IDispatch`-Schnittstelle und die zugeordnete `ITypeInfo` Schnittstelle kann der Host Skript Methoden aufrufen oder Skript Variablen anzeigen und ändern.  
  
 `ppdisp`  
 vorgenommen Adresse einer Variablen, die einen Zeiger auf das-Objekt empfängt, das den globalen Methoden und Eigenschaften des Skripts zugeordnet ist. Wenn ein solches Objekt von der Skript-Engine nicht unterstützt wird, wird `NULL` zurückgegeben.  
  
## <a name="return-value"></a>Rückgabewert  
 Gibt einen der folgenden Werte zurück:  
  
|Rückgabewert|Bedeutung|  
|------------------|-------------|  
|`S_OK`|Erfolgreich.|  
|`E_INVALIDARG`|Ein Argument war ungültig.|  
|`E_POINTER`|Es wurde ein ungültiger Zeiger angegeben.|  
|`E_UNEXPECTED`|Der-Befehl wurde nicht erwartet (z. b. wurde die Skript-Engine noch nicht geladen oder initialisiert).|  
|`S_FALSE`|Die Skript-Engine unterstützt kein dispatchobjekt. der `ppdisp`-Parameter ist auf NULL festgelegt.|  
  
## <a name="remarks"></a>Hinweise  
 Da Methoden und Eigenschaften durch Aufrufen der [iactivescriptparamese](../../winscript/reference/iactivescriptparse.md) -Schnittstelle hinzugefügt werden können, kann die von dieser Methode zurückgegebene `IDispatch`-Schnittstelle neue Methoden und Eigenschaften dynamisch unterstützen. Ebenso sollte die `IDispatch::GetTypeInfo` Methode eine neue, eindeutige `ITypeInfo` Schnittstelle zurückgeben, wenn Methoden und Eigenschaften hinzugefügt werden. Beachten Sie jedoch, dass die Sprachmodule die `IDispatch` Schnittstelle nicht so ändern dürfen, dass Sie nicht mit einer früheren `ITypeInfo` zurückgegebenen Schnittstelle kompatibel ist. Dies impliziert beispielsweise, dass DispIds nie wieder verwendet werden.  
  
## <a name="see-also"></a>Siehe auch  
 [IActiveScript](../../winscript/reference/iactivescript.md)