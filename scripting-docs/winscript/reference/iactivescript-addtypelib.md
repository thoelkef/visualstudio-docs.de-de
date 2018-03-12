---
title: IActiveScript::AddTypeLib | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- IActiveScript.AddTypeLib
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScript_AddTypeLib
ms.assetid: 8e507ea8-c80a-471c-b482-ae753c6e8595
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a2be7cf033b4b5dd4d99b19a3b71ed53e32af855
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptaddtypelib"></a>IActiveScript::AddTypeLib
Der Namespace für das Skript wird eine Typbibliothek hinzugefügt. Dies ist vergleichbar mit der `#include` in C/C++-Richtlinie. Sie ermöglicht eine Reihe von vordefinierten Elemente wie Klassendefinitionen, `typedefs`, und benannte Konstanten für das Skript verfügbar Laufzeitumgebung hinzugefügt werden.  
  
## <a name="syntax"></a>Syntax  
  
```  
HRESULT AddTypeLib(  
    REFGUID guidTypeLib,  // CLSID of type library  
    DWORD dwMaj,          // major version number  
    DWORD dwMin,          // minor version number  
    DWORD dwFlags         // option flags  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `guidTypeLib`  
 [in] Die CLSID der Typbibliothek hinzufügen.  
  
 `dwMaj`  
 [in] Die Hauptversionsnummer.  
  
 `dwMin`  
 [in] Nummer der Nebenversion.  
  
 `dwFlags`  
 [in] Flags-Option. Folgendes kann sein:  
  
|Wert|Bedeutung|  
|-----------|-------------|  
|SCRIPTTYPELIB_ISCONTROL|Die Typbibliothek wird beschrieben, ein ActiveX-Steuerelement, die vom Host verwendet wird.|  
  
## <a name="return-value"></a>Rückgabewert  
 Gibt einen der folgenden Werte zurück:  
  
|Rückgabewert|Bedeutung|  
|------------------|-------------|  
|`S_OK`|Erfolgreich.|  
|`E_INVALIDARG`|Ein Argument war ungültig.|  
|`E_UNEXPECTED`|Der Aufruf wurde nicht erwartet (z. B. das Skriptmodul wurde noch kein geladen oder initialisiert).|  
|`TYPE_E_CANTLOADLIBRARY`|Die angegebene Typbibliothek konnte nicht geladen werden.|  
  
## <a name="see-also"></a>Siehe auch  
 [IActiveScript](../../winscript/reference/iactivescript.md)