---
title: 'IActiveScript:: Clone | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScript.Clone
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScript_Clone
ms.assetid: aa000b2a-7085-448d-a422-f7adac7851cb
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 084da486d2e5831176130ccd080b9e09a80c9bcc
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/08/2019
ms.locfileid: "54093664"
---
# <a name="iactivescriptclone"></a>IActiveScript::Clone
Klont die aktuelle Skript-Engine (minus alle aktuellen Ausführungsstatus), eine geladene Skript-Engine, die keine Standort in den aktuellen Thread zurückgibt. Die Eigenschaften dieses neue Skriptmodul werden mit den Eigenschaften identisch sein, die, denen die ursprüngliche Skript-Engine in wäre, wenn sie zurück zum initialisierten Zustand umgestellt wurden.  
  
## <a name="syntax"></a>Syntax  
  
```cpp
HRESULT Clone(  
    IActiveScript **ppscript  // receives pointer to IActiveScript  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `ppscript`  
 [out] Adresse einer Variablen, die einen Zeiger auf empfängt die [IActiveScript](../../winscript/reference/iactivescript.md) Schnittstelle des geklonten Skript-Engine. Der Host muss erstellt werden, ein Standort, und rufen die [IActiveScript::SetScriptSite](../../winscript/reference/iactivescript-setscriptsite.md) Methode für das neue Skriptmodul, damit es im initialisierten Zustand ist und daher verwendet werden.  
  
## <a name="return-value"></a>Rückgabewert  
 Gibt einen der folgenden Werte zurück:  
  
|Rückgabewert|Bedeutung|  
|------------------|-------------|  
|`S_OK`|Erfolgreich.|  
|`E_NOTIMPL`|Diese Methode wird nicht unterstützt.|  
|`E_POINTER`|Es wurde ein ungültiger Zeiger angegeben.|  
|`E_UNEXPECTED`|Der Aufruf wurde nicht erwartet (z. B. die Skript-Engine wurde noch nicht wurden geladen oder initialisiert).|  
  
## <a name="remarks"></a>Hinweise  
 Die `IActiveScript::Clone` Methode ist eine Optimierung der `IPersist*::Save`, `CoCreateInstance`, und `IPersist*::Load`, sodass Sie der Status der neuen Skript-Engine identisch sein sollte, als ob der Zustand der ursprünglichen Skript-Engine gespeichert und in eine neue Skript-Engine geladen wurden. Benannte Elemente in der geklonten Skript-Engine dupliziert werden, aber bestimmte Objektzeiger für jedes Element vergessen werden, und erhalten Sie mit der [iactivescriptsite:: GetItemInfo](../../winscript/reference/iactivescriptsite-getiteminfo.md) Methode. Dadurch wird ein identische Objektmodell für pro-Thread-Einstiegspunkte (eines Apartmentmodells) verwendet werden.  
  
 Diese Methode wird für Multithread-Server-Hosts verwendet, die mehrere Instanzen des gleichen Skripts ausgeführt werden können. Die Skript-Engine kann zurückgeben `E_NOTIMPL`, in diesem Fall der Host das gleiche Ergebnis erzielen kann, durch Duplizieren des persistenten Status, und erstellen eine neue Instanz der Skript-Engine mit einer `IPersist*` Schnittstelle.  
  
 Diese Methode kann von nicht-Base Threads aufgerufen werden, ohne dass eine nicht-Base-Legende Hostobjekte oder in der [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md) Schnittstelle.  
  
## <a name="see-also"></a>Siehe auch  
 [IActiveScript](../../winscript/reference/iactivescript.md)