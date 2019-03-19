---
title: IActiveScript::AddTypeLib | Microsoft-Dokumentation
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
ms.openlocfilehash: c4943d1305c2f25de4eec9e782949a66827de879
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/19/2019
ms.locfileid: "58144874"
---
# <a name="iactivescriptaddtypelib"></a>IActiveScript::AddTypeLib
Der Namespace für das Skript wird eine Typbibliothek hinzugefügt. Dies ist vergleichbar mit der `#include` in C/C++-Direktive. Sie können einen Satz von vordefinierten Elemente aus, wie z. B. Klassendefinitionen, `typedefs`, und benannte Konstanten, die Laufzeitumgebung verfügbar, um das Skript hinzugefügt werden.  
  
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
 [in] Die CLSID der Typbibliothek hinzufügen.  
  
 `dwMaj`  
 [in] Hauptversionsnummer.  
  
 `dwMin`  
 [in] Nummer der Nebenversion.  
  
 `dwFlags`  
 [in] Optionsflags. Folgendes kann sein:  
  
|Wert|Bedeutung|  
|-----------|-------------|  
|SCRIPTTYPELIB_ISCONTROL|Die Typbibliothek beschreibt ein ActiveX-Steuerelement, die vom Host verwendet wird.|  
  
## <a name="return-value"></a>Rückgabewert  
 Gibt einen der folgenden Werte zurück:  
  
|Rückgabewert|Bedeutung|  
|------------------|-------------|  
|`S_OK`|Erfolgreich.|  
|`E_INVALIDARG`|Ein Argument war ungültig.|  
|`E_UNEXPECTED`|Der Aufruf wurde nicht erwartet (z. B. die Skript-Engine wurde noch nicht wurden geladen oder initialisiert).|  
|`TYPE_E_CANTLOADLIBRARY`|Die angegebene Typbibliothek konnte nicht geladen werden.|  
  
## <a name="see-also"></a>Siehe auch  
 [IActiveScript](../../winscript/reference/iactivescript.md)