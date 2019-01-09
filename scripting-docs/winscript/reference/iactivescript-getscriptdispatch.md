---
title: Getscriptdispatch | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: 2a18d6781ca2b7820686b317ad0be5da425ade1f
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/08/2019
ms.locfileid: "54097681"
---
# <a name="iactivescriptgetscriptdispatch"></a>IActiveScript::GetScriptDispatch
Ruft die `IDispatch` Schnittstelle für die Methoden und Eigenschaften, die dem derzeit ausgeführten Skript zugeordnet.  
  
## <a name="syntax"></a>Syntax  
  
```cpp
HRESULT GetScriptDispatch(  
    LPCOLESTR pstrItemName  // address of item name  
    IDispatch **ppdisp      // receives IDispatch pointer  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pstrItemName`  
 [in] Die Adresse eines Puffers, der den Namen des Elements enthält, für den benötigt der Aufrufer auf den zugeordneten DispatchRuntime-Objekt. Wenn dieser Parameter ist `NULL`, das DispatchRuntime-Objekt enthält, deren Mitglieder alle globalen Methoden und Eigenschaften durch das Skript definiert. Durch die `IDispatch` -Schnittstelle und den zugehörigen `ITypeInfo` -Schnittstelle, der Host Skriptmethoden oder Ansicht aufrufen kann, und Ändern von Skriptvariablen.  
  
 `ppdisp`  
 [out] Die Adresse einer Variablen, die einen Zeiger auf das globale Methoden und Eigenschaften des Skripts zugeordnete Objekt empfängt. Wenn ein Objekt, von die Skript-Engine nicht unterstützt wird `NULL` zurückgegeben wird.  
  
## <a name="return-value"></a>Rückgabewert  
 Gibt einen der folgenden Werte zurück:  
  
|Rückgabewert|Bedeutung|  
|------------------|-------------|  
|`S_OK`|Erfolgreich.|  
|`E_INVALIDARG`|Ein Argument war ungültig.|  
|`E_POINTER`|Es wurde ein ungültiger Zeiger angegeben.|  
|`E_UNEXPECTED`|Der Aufruf wurde nicht erwartet (z. B. die Skript-Engine wurde noch nicht wurden geladen oder initialisiert).|  
|`S_FALSE`|Die Skript-Engine unterstützt nicht die Dispatch-Objekt. die `ppdisp` Parameter auf NULL festgelegt ist.|  
  
## <a name="remarks"></a>Hinweise  
 Da durch Aufrufen von Methoden und Eigenschaften hinzugefügt werden können die [IActiveScriptParse](../../winscript/reference/iactivescriptparse.md) -Schnittstelle, die `IDispatch` Schnittstelle, die von dieser Methode zurückgegebene kann dynamisch neue Methoden und Eigenschaften zu unterstützen. Auf ähnliche Weise die `IDispatch::GetTypeInfo` -Methode gibt einen neuen, eindeutigen `ITypeInfo` -Schnittstelle auf, wenn die Methoden und Eigenschaften hinzugefügt werden. Beachten Sie jedoch, dass Sprach-Engines nicht geändert werden darf die `IDispatch` -Schnittstelle in einer Weise inkompatibel mit allen vorherigen `ITypeInfo` -Schnittstelle zurückgegeben wird. Dies bedeutet beispielsweise, dass die DISPIDs nie wiederverwendet werden.  
  
## <a name="see-also"></a>Siehe auch  
 [IActiveScript](../../winscript/reference/iactivescript.md)