---
title: IActiveScriptAuthor::GetLanguageFlags | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptAuthor.GetLanguageFlags
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptAuthor::GetLanguageFlags
ms.assetid: eb244452-62f7-4a73-b48f-1aa05cbcc32d
caps.latest.revision: 14
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6137f1cd77d2f305a9ff9d51ac49c214e4c4237b
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
ms.locfileid: "24645540"
---
# <a name="iactivescriptauthorgetlanguageflags"></a>IActiveScriptAuthor::GetLanguageFlags
Gibt Informationen zurück.  
  
## <a name="syntax"></a>Syntax  
  
```  
HRESULT GetLanguageFlags(  
   DWORD              *pgrfasa  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pgrfasa`  
 [out] Die Flags, die Language-Informationen enthalten. Eine Kombination der folgenden Werte ist möglich:  
  
|Konstante|Wert|Beschreibung|  
|--------------|-----------|-----------------|  
|fasaPreferInternalHandler|0 x 0001|Die Sprache bevorzugt Erstellung von Ereignishandler Skript unter Verwendung des Skripts Modul anstelle der Anwendung zu erstellen.|  
|fasaSupportInternalHandler|0 x 0002|Die Sprache unterstützt Skript-Ereignishandler, die vom Datenbankmodul authoring Skript erstellt.|  
|fasaCaseSensitive|0 x 0004|Die Skriptsprache ist Groß-/Kleinschreibung beachtet.|  
  
## <a name="return-value"></a>Rückgabewert  
 Eine `HRESULT`. Mögliches Werte (aber nicht die Einzigen) sind die in der folgenden Tabelle.  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
  
## <a name="remarks"></a>Hinweise  
 Wenn das Skript authoring Modul Ereignishandler verwaltet, sollte Ihre Anwendung aufrufen `CreateChildHandler` aus einem `IScriptEntry` Objekt. Dies erstellt ein `IScriptScriptlet` -Objekt, das an den Ereignishandler entspricht. Das Modul fügt auch einen Ereignishandler hinzu, um den Skripteintrag. Der Ereignishandler ist eine leere Funktion, die Informationen für die angegebene Signatur enthält.  
  
 Wenn Ihre Anwendung Ereignishandler verwaltet werden, rufen sie `CreateChildHandler` aus einem `IScriptNode` Objekt, das eine Ereignis-Handler-Scriptlet darstellt. Dies erstellt ein `IScriptScriptlet` -Objekt, das die Ereignis-Handler-Scriptlet zugeordnet ist. Die Anwendung muss außerdem eine leere Funktion als ein Ereignis hinzufügen Handler, ein neues oder vorhandenes `IScriptEntry` Objekt.  
  
## <a name="see-also"></a>Siehe auch  
 [IActiveScriptAuthor-Schnittstelle](../../winscript/reference/iactivescriptauthor-interface.md)