---
title: IActiveScript::GetScriptDispatch | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- IActiveScript.GetScriptDispatch
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScript_GetScriptDispatch
ms.assetid: 2092ccd4-1f4c-493a-b5b7-077a70ce95ca
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5b2f09934cf6d2bb28f7dae93d0bf49c8dc7437d
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptgetscriptdispatch"></a>IActiveScript::GetScriptDispatch
Ruft die `IDispatch` Schnittstelle für die Methoden und Eigenschaften, die den derzeit ausgeführten Skript zugeordnet.  
  
## <a name="syntax"></a>Syntax  
  
```  
HRESULT GetScriptDispatch(  
    LPCOLESTR pstrItemName  // address of item name  
    IDispatch **ppdisp      // receives IDispatch pointer  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pstrItemName`  
 [in] Die Adresse eines Puffers, der den Namen des Elements enthält, für die der Aufrufer die zugeordneten DispatchRuntime-Objekt benötigt. Wenn dieser Parameter ist `NULL`, DispatchRuntime-Objekt enthält, deren Mitglieder alle globalen Methoden und Eigenschaften, unter Verwendung des Skripts definiert. Über die `IDispatch` Schnittstelle und den zugehörigen `ITypeInfo` -Schnittstelle, der Host Skriptmethoden oder Ansicht aufrufen und Skriptvariablen ändern kann.  
  
 `ppdisp`  
 [out] Die Adresse einer Variablen, die empfängt einen Zeiger auf das Objekt, das das Skript globale Methoden und Eigenschaften zugeordnet. Wenn das Skriptmodul solches Objekt nicht unterstützt `NULL` zurückgegeben wird.  
  
## <a name="return-value"></a>Rückgabewert  
 Gibt einen der folgenden Werte zurück:  
  
|Rückgabewert|Bedeutung|  
|------------------|-------------|  
|`S_OK`|Erfolgreich.|  
|`E_INVALIDARG`|Ein Argument war ungültig.|  
|`E_POINTER`|Es wurde ein ungültiger Zeiger angegeben.|  
|`E_UNEXPECTED`|Der Aufruf wurde nicht erwartet (z. B. das Skriptmodul wurde noch kein geladen oder initialisiert).|  
|`S_FALSE`|Das Skriptmodul unterstützt keine Dispatch-Objekt; die `ppdisp` Parameter auf NULL festgelegt ist.|  
  
## <a name="remarks"></a>Hinweise  
 Da durch Aufrufen von Methoden und Eigenschaften hinzugefügt werden können die [IActiveScriptParse](../../winscript/reference/iactivescriptparse.md) -Schnittstelle, die `IDispatch` von dieser Methode zurückgegebene Schnittstelle kann dynamisch unterstützen, neue Methoden und Eigenschaften. Auf ähnliche Weise die `IDispatch::GetTypeInfo` -Methode zurückgeben sollte eine neue, eindeutige `ITypeInfo` Benutzeroberfläche, Eigenschaften und Methoden hinzugefügt werden. Beachten Sie jedoch, dass Sprache-Module nicht geändert werden darf die `IDispatch` -Schnittstelle in der Weise, d. h. kompatibel mit allen vorherigen `ITypeInfo` Schnittstelle zurückgegeben. Dies impliziert z. B., dass DISPIDs nie wiederverwendet werden.  
  
## <a name="see-also"></a>Siehe auch  
 [IActiveScript](../../winscript/reference/iactivescript.md)