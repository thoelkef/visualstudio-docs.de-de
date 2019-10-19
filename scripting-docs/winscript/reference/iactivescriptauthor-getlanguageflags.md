---
title: 'Iactivescriptauthor:: getlanguageflags | Microsoft-Dokumentation'
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
ms.openlocfilehash: 68da16513050bd87642be2c96212a330a0916608
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/18/2019
ms.locfileid: "72576200"
---
# <a name="iactivescriptauthorgetlanguageflags"></a>IActiveScriptAuthor::GetLanguageFlags
Gibt Sprachinformationen zurück.  
  
## <a name="syntax"></a>Syntax  
  
```cpp
HRESULT GetLanguageFlags(  
   DWORD              *pgrfasa  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pgrfasa`  
 vorgenommen Die Flags, die Sprachinformationen enthalten. Kann eine Kombination der folgenden Werte sein:  
  
|Konstante|Wert|Beschreibung|  
|--------------|-----------|-----------------|  
|fasapreferinternalhandler|0x0001|Die Sprache bevorzugt die Erstellung von Skript Ereignis Handlern durch das Skript Erstellungs Modul anstelle der Anwendung.|  
|fasasupportinternalhandler|0x0002|Die Sprache unterstützt Skript Ereignishandler, die von der Skript Erstellungs-Engine erstellt wurden.|  
|fasacasesensitive|0x0004|Bei der Skriptsprache wird Groß-/Kleinschreibung beachtet.|  
  
## <a name="return-value"></a>Rückgabewert  
 Eine `HRESULT`. Mögliches Werte (aber nicht die Einzigen) sind die in der folgenden Tabelle.  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
  
## <a name="remarks"></a>Hinweise  
 Wenn die Skript Erstellungs-Engine Ereignishandler verwaltet, sollte Ihre Anwendung `CreateChildHandler` von einem `IScriptEntry`-Objekt aus abrufen. Dadurch wird ein `IScriptScriptlet` Objekt erstellt, das dem Ereignishandler entspricht. Die Engine fügt dem Skript Eintrag außerdem einen Ereignishandler hinzu. Der Ereignishandler ist eine leere Funktion, die die angegebenen Signatur Informationen enthält.  
  
 Wenn Ihre Anwendung Ereignishandler verwaltet, sollte Sie `CreateChildHandler` von einem `IScriptNode` Objekt aus aufgerufen werden, das ein ereignishandlerscriptlet darstellt. Dadurch wird ein `IScriptScriptlet` Objekt erstellt, das dem Ereignishandler-Scriptlet zugeordnet ist. Die Anwendung muss auch einer neuen oder vorhandenen `IScriptEntry` Objekt eine leere Funktion als Ereignishandler hinzufügen.  
  
## <a name="see-also"></a>Siehe auch  
 [IActiveScriptAuthor-Schnittstelle](../../winscript/reference/iactivescriptauthor-interface.md)