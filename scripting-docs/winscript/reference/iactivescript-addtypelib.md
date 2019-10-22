---
title: 'IActiveScript:: addtypelib | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScript.AddTypeLib
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScript_AddTypeLib
ms.assetid: 8e507ea8-c80a-471c-b482-ae753c6e8595
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 254a5133d42689020eaaae290a1016de4b848100
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575813"
---
# <a name="iactivescriptaddtypelib"></a>IActiveScript::AddTypeLib
Fügt dem namens Bereich für das Skript eine Typbibliothek hinzu. Dies ähnelt der `#include`-Direktive in C/C++. Sie ermöglicht das Hinzufügen eines Satzes vordefinierter Elemente, wie z. b. Klassendefinitionen, `typedefs` und benannte Konstanten, zur Laufzeitumgebung, die für das Skript verfügbar ist.  
  
## <a name="syntax"></a>Syntax  
  
```cpp
HRESULT AddTypeLib(  
    REFGUID guidTypeLib,  // CLSID of type library  
    DWORD dwMaj,          // major version number  
    DWORD dwMin,          // minor version number  
    DWORD dwFlags         // option flags  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `guidTypeLib`  
 in CLSID der hinzu zufügenden Typbibliothek.  
  
 `dwMaj`  
 in Hauptversionsnummer.  
  
 `dwMin`  
 in Neben Versionsnummer.  
  
 `dwFlags`  
 in Optionsflags. Folgende Aktionen sind möglich:  
  
|Wert|Bedeutung|  
|-----------|-------------|  
|SCRIPTTYPELIB_ISCONTROL|Die Typbibliothek beschreibt ein vom Host verwendetes ActiveX-Steuerelement.|  
  
## <a name="return-value"></a>Rückgabewert  
 Gibt einen der folgenden Werte zurück:  
  
|Rückgabewert|Bedeutung|  
|------------------|-------------|  
|`S_OK`|Erfolgreich.|  
|`E_INVALIDARG`|Ein Argument war ungültig.|  
|`E_UNEXPECTED`|Der-Befehl wurde nicht erwartet (z. b. wurde die Skript-Engine noch nicht geladen oder initialisiert).|  
|`TYPE_E_CANTLOADLIBRARY`|Die angegebene Typbibliothek konnte nicht geladen werden.|  
  
## <a name="see-also"></a>Siehe auch  
 [IActiveScript](../../winscript/reference/iactivescript.md)