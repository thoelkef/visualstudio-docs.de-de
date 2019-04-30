---
title: IActiveScriptAuthor::GetLanguageFlags | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/18/2017
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
ms.openlocfilehash: d9f1a68db05ac0d909108ce77587ae4b071c9a2b
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62935470"
---
# <a name="iactivescriptauthorgetlanguageflags"></a>IActiveScriptAuthor::GetLanguageFlags
Gibt die Language-Informationen zurück.  
  
## <a name="syntax"></a>Syntax  
  
```cpp
HRESULT GetLanguageFlags(  
   DWORD              *pgrfasa  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pgrfasa`  
 [out] Die Flags, die Language-Informationen enthalten. Eine Kombination der folgenden Werte sind möglich:  
  
|Konstante|Wert|Beschreibung|  
|--------------|-----------|-----------------|  
|fasaPreferInternalHandler|0x0001|Die Sprache bevorzugt Skript Event Handler erstellen, von dem Skript-Engine-, anstatt die Anwendung erstellen.|  
|fasaSupportInternalHandler|0x0002|Die Sprache unterstützt die Skript-Ereignishandler, die vom Skript-Engine-Erstellung erstellt.|  
|fasaCaseSensitive|0x0004|Die Skriptsprache ist Groß-/Kleinschreibung beachtet.|  
  
## <a name="return-value"></a>Rückgabewert  
 Eine `HRESULT`. Mögliches Werte (aber nicht die Einzigen) sind die in der folgenden Tabelle.  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
  
## <a name="remarks"></a>Hinweise  
 Wenn das Skript-Engine-erstellen-Ereignishandler verwaltet werden, sollte Ihre Anwendung aufrufen `CreateChildHandler` aus einem `IScriptEntry` Objekt. Dies erstellt eine `IScriptScriptlet` Objekt, das den Ereignishandler entspricht. Die Engine fügt auch einen Ereignishandler auf den Skripteintrag hinzu. Der Ereignishandler ist eine leere Funktion, die Informationen für die angegebene Signatur enthält.  
  
 Wenn Ihre Anwendung Ereignishandler verwaltet werden, sollte es aufrufen `CreateChildHandler` aus einem `IScriptNode` Objekt, das ein Ereignis-Handler-Scriptlet darstellt. Dies erstellt eine `IScriptScriptlet` -Objekt, das die Ereignis-Handler-Scriptlet zugeordnet ist. Die Anwendung bietet außerdem eine leere Funktion als ein Ereignis hinzufügen Handler, der eine neue oder vorhandene `IScriptEntry` Objekt.  
  
## <a name="see-also"></a>Siehe auch  
 [IActiveScriptAuthor-Schnittstelle](../../winscript/reference/iactivescriptauthor-interface.md)