---
title: "IActiveScript::GetScriptDispatch | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScript.GetScriptDispatch
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IActiveScript_GetScriptDispatch"
ms.assetid: 2092ccd4-1f4c-493a-b5b7-077a70ce95ca
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IActiveScript::GetScriptDispatch
Ruft die `IDispatch`\-Schnittstelle für die Methoden und Eigenschaften ab, die dem derzeit ausgeführten Skript zugeordnet sind.  
  
## Syntax  
  
```  
HRESULT GetScriptDispatch(  
    LPCOLESTR pstrItemName  // address of item name  
    IDispatch **ppdisp      // receives IDispatch pointer  
);  
```  
  
#### Parameter  
 `pstrItemName`  
 \[in\] Adresse eines Puffers, der den Namen des Elements enthält, für das der Aufrufer das zugeordnete Dispatchobjekt erfordert.  Wenn dieser Parameter `NULL` ist, enthält das Dispatchobjekt als Member alle globalen Methoden und Eigenschaften definierten durch das Skript.  Durch die `IDispatch`\-Schnittstelle und die zugeordnete `ITypeInfo`\-Schnittstelle kann der Host Skriptmethoden oder \-Ansicht aufrufen und Skriptvariablen ändern.  
  
 `ppdisp`  
 \[out\] Zugeordnete Adresse einer Variablen, die einen Zeiger auf das Objekt empfängt, des globalen mit den Methoden und Eigenschaften Skripts auf.  Wenn das Skriptmodul kein solches Objekt unterstützt, wird `NULL` zurückgegeben.  
  
## Rückgabewert  
 Gibt eine der folgenden Werte:  
  
|Rückgabewert|Bedeutung|  
|------------------|---------------|  
|`S_OK`|Erfolgreich.|  
|`E_INVALIDARG`|Ein Argument war ungültig.|  
|`E_POINTER`|Ein ungültiger Zeiger wurde angegeben.|  
|`E_UNEXPECTED`|Der Aufruf wurde nicht erwartet \(beispielsweise, ist das Skriptmodul noch nicht geladen wurde oder initialisiert wurden\).|  
|`S_FALSE`|Das Skriptmodul unterstützt kein Dispatchobjekt; der `ppdisp`\-Parameter wird festgelegt, um auf NULL.|  
  
## Hinweise  
 Da Methoden und Eigenschaften hinzugefügt werden können, indem die [IActiveScriptParse](../../winscript/reference/iactivescriptparse.md)\-Schnittstelle aufruft, kann die `IDispatch`\-Schnittstelle, die zurückgegeben wird neue Methoden und Eigenschaften darin, dynamisch unterstützen.  Ähnlich sollte die `IDispatch::GetTypeInfo`\-Methode eine neue, eindeutige `ITypeInfo`\-Schnittstelle zurückgeben, wenn Methoden und Eigenschaften hinzugefügt werden.  Beachten Sie jedoch die Sprachmodule die `IDispatch`\-Schnittstelle nicht auf eine Weise ändern dürfen, die jeder vorherigen zurückgegebenen `ITypeInfo`\-Schnittstelle nicht kompatibel ist.  Das bedeutet beispielsweise dass DISPID nie wiederverwendet wird.  
  
## Siehe auch  
 [IActiveScript](../../winscript/reference/iactivescript.md)