---
title: IVariantChangeType::ChangeType | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IVariantChangeType.ChangeType
apilocation:
- scrobj.dll
helpviewer_keywords:
- IVariantChangeType::ChangeType
ms.assetid: 52374764-c42e-49af-a219-ee00c535a118
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0a02b8a3991ff6d20370cd4a2ea4cd87aa9a1226
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/08/2019
ms.locfileid: "54086579"
---
# <a name="ivariantchangetypechangetype"></a>IVariantChangeType::ChangeType
Akzeptiert einen Varianten-Wert, und erstellt eine neue Variante mit einem angegebenen Typ.  
  
## <a name="syntax"></a>Syntax  
  
```cpp
HRESULT ChangeType(  
   VARIANT*  pvarDst,  
   VARIANT*  pvarSrc,  
   LCID  lcid,  
   VARTYPE  vtNew  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pvarDst`  
 [in, out] Eine Variante durch dargestellten Wert enthält `pvarSrc`, jedoch mit den vom angegebenen Typ `vtNew`.  
  
 `pvarSrc`  
 [in] Ein variant-Wert in einen neuen Typ zu ändern.  
  
 `lcid`  
 [in] Der Gebietsschemakontext zu verwenden, wenn die Argumente zu oder von Zeichenfolgen zu konvertieren.  
  
 `vtNew`  
 [in] Gibt den Typ für `pvarDst` werden.  
  
## <a name="return-value"></a>Rückgabewert  
 Die Methode gibt ein `HRESULT` zurück. Mögliches Werte (aber nicht die Einzigen) sind die in der folgenden Tabelle.  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
  
## <a name="remarks"></a>Hinweise  
 Die `pvarDst` und `pvarSrc` Argumente möglicherweise gleich ist, in diesem Fall wird der ursprüngliche Wert überschrieben. Diese Methode übergibt `pvarDst` auf die `VariantClear` -Funktion, und folglich `pvarDst` auf einen gültigen Wert initialisiert werden soll.  
  
## <a name="see-also"></a>Siehe auch  
 [IVariantChangeType-Schnittstelle](../../winscript/reference/ivariantchangetype-interface.md)