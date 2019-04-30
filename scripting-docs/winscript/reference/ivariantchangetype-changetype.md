---
title: IVariantChangeType::ChangeType | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/18/2017
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
ms.openlocfilehash: 81ed0a8502e9b0cfc53725621d477d34ee5010ea
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62945633"
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