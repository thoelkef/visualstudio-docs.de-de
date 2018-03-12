---
title: IActiveScript::Clone | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- IActiveScript.Clone
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScript_Clone
ms.assetid: aa000b2a-7085-448d-a422-f7adac7851cb
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 4b0b83bcf86bcc56701d11f22640df966334697b
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptclone"></a>IActiveScript::Clone
Klont das aktuelle Skriptmodul (minus alle aktuellen Ausführungsstatus), Rückgabe einer geladenen Skriptmodul, die keine Standort in den aktuellen Thread verfügt. Die Eigenschaften dieser neuen Skriptmodul werden an den Eigenschaften identisch sein, denen das ursprüngliche Skriptmodul in wäre, wenn wurden Übergang zurück zum initialisierten Zustand.  
  
## <a name="syntax"></a>Syntax  
  
```  
HRESULT Clone(  
    IActiveScript **ppscript  // receives pointer to IActiveScript  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `ppscript`  
 [out] Adresse einer Variablen, die einen Zeiger auf empfängt die [IActiveScript](../../winscript/reference/iactivescript.md) Schnittstelle des geklonten verwendeten Skriptmoduls. Der Host muss erstellen Sie eine Website aus und rufen die [IActiveScript::SetScriptSite](../../winscript/reference/iactivescript-setscriptsite.md) Methode auf das neue Skriptmodul, damit es im initialisierten Zustand ist und somit verwendet werden kann.  
  
## <a name="return-value"></a>Rückgabewert  
 Gibt einen der folgenden Werte zurück:  
  
|Rückgabewert|Bedeutung|  
|------------------|-------------|  
|`S_OK`|Erfolgreich.|  
|`E_NOTIMPL`|Diese Methode wird nicht unterstützt.|  
|`E_POINTER`|Es wurde ein ungültiger Zeiger angegeben.|  
|`E_UNEXPECTED`|Der Aufruf wurde nicht erwartet (z. B. das Skriptmodul wurde noch kein geladen oder initialisiert).|  
  
## <a name="remarks"></a>Hinweise  
 Die `IActiveScript::Clone` Methode ist eine Optimierung der `IPersist*::Save`, `CoCreateInstance`, und `IPersist*::Load`, sodass der Status des verwendeten Skriptmoduls neue identisch sein sollte, als ob der Zustand der ursprünglichen verwendeten Skriptmoduls gespeichert und in ein neues Skriptmodul geladen wurden. Benannte Elemente werden in der geklonten Skriptmodul dupliziert, aber bestimmten Objektzeigern für jedes Element werden vergessen und erhalten Sie mit der [IActiveScriptSite::GetItemInfo](../../winscript/reference/iactivescriptsite-getiteminfo.md) Methode. Dadurch wird eine identische Objektmodell mit threadspezifisches Einstiegspunkte (eines Apartmentmodells) verwendet werden.  
  
 Diese Methode wird für Multithread-Server-Hosts verwendet, die mehrere Instanzen des gleichen Skripts ausgeführt werden kann. Das Skriptmodul gelegten `E_NOTIMPL`, in diesem Fall der Host das gleiche Ergebnis erzielen kann, durch Duplizieren des persistenten Status, und erstellen eine neue Instanz des verwendeten Skriptmoduls mit einer `IPersist*` Schnittstelle.  
  
 Diese Methode kann von nicht zur Basis Threads aufgerufen werden, ohne dass eine Legende nicht zur Basis Hostobjekte oder in der [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md) Schnittstelle.  
  
## <a name="see-also"></a>Siehe auch  
 [IActiveScript](../../winscript/reference/iactivescript.md)