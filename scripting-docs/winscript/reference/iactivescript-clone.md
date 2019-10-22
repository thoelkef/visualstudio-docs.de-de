---
title: 'IActiveScript:: Clone | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 01/18/2017
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
ms.openlocfilehash: fbaad29cb31af26a0f26a1c679a900192fc77041
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575796"
---
# <a name="iactivescriptclone"></a>IActiveScript::Clone
Klont die aktuelle Skript-Engine (abzüglich jedes aktuellen Ausführungs Zustands) und gibt eine geladene Skript-Engine zurück, die über keine Site im aktuellen Thread verfügt. Die Eigenschaften dieser neuen Skript-Engine sind identisch mit den Eigenschaften, in denen sich die ursprüngliche Skript-Engine befindet, wenn Sie in den initialisierten Zustand zurückversetzt wurde.  
  
## <a name="syntax"></a>Syntax  
  
```cpp
HRESULT Clone(  
    IActiveScript **ppscript  // receives pointer to IActiveScript  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `ppscript`  
 vorgenommen Adresse einer Variablen, die einen Zeiger auf die [IActiveScript](../../winscript/reference/iactivescript.md) -Schnittstelle der geklonten Skript-Engine empfängt. Der Host muss eine Website erstellen und die [IActiveScript:: setscriptsite](../../winscript/reference/iactivescript-setscriptsite.md) -Methode für die neue Skript-Engine aufrufen, bevor Sie sich im initialisierten Zustand befindet und daher verwendbar ist.  
  
## <a name="return-value"></a>Rückgabewert  
 Gibt einen der folgenden Werte zurück:  
  
|Rückgabewert|Bedeutung|  
|------------------|-------------|  
|`S_OK`|Erfolgreich.|  
|`E_NOTIMPL`|Diese Methode wird nicht unterstützt.|  
|`E_POINTER`|Es wurde ein ungültiger Zeiger angegeben.|  
|`E_UNEXPECTED`|Der-Befehl wurde nicht erwartet (z. b. wurde die Skript-Engine noch nicht geladen oder initialisiert).|  
  
## <a name="remarks"></a>Hinweise  
 Die `IActiveScript::Clone`-Methode ist eine Optimierung von `IPersist*::Save`, `CoCreateInstance` und `IPersist*::Load`, sodass der Status der neuen Skript-Engine identisch sein sollte, wenn der Status der ursprünglichen Skript-Engine gespeichert und in eine neue Skript-Engine geladen wurde. Benannte Elemente werden in der geklonten Skript-Engine dupliziert, aber bestimmte Objekt Zeiger für jedes Element werden vergessen und mit der [iactivescriptsite:: getiteminfo](../../winscript/reference/iactivescriptsite-getiteminfo.md) -Methode abgerufen. Dadurch kann ein identisches Objektmodell mit Thread spezifischen Einstiegspunkten (einem Apartment Modell) verwendet werden.  
  
 Diese Methode wird für Multithread-Server Hosts verwendet, die mehrere Instanzen desselben Skripts ausführen können. Die Skript-Engine gibt möglicherweise `E_NOTIMPL` zurück. in diesem Fall kann der Host dasselbe Ergebnis erzielen, indem der persistente Zustand duplizieren und eine neue Instanz der Skript-Engine mit einer `IPersist*` Schnittstelle erstellt wird.  
  
 Diese Methode kann von nicht basisthreads aus aufgerufen werden, ohne dass ein Aufruf von Objekten oder die [iactivescriptsite](../../winscript/reference/iactivescriptsite.md) -Schnittstelle durchgeführt werden soll.  
  
## <a name="see-also"></a>Siehe auch  
 [IActiveScript](../../winscript/reference/iactivescript.md)