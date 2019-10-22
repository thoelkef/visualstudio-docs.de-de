---
title: 'Ivariantchangetype:: ChangeType | Microsoft-Dokumentation'
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
ms.openlocfilehash: 406d5d8486b3016f0105b7bd8bf231db0e1e9613
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/18/2019
ms.locfileid: "72571781"
---
# <a name="ivariantchangetypechangetype"></a>IVariantChangeType::ChangeType
Nimmt einen Variant-Wert und erstellt eine neue Variante mit einem angegebenen Typ.  
  
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
 [in, out] Eine Variante, die den durch `pvarSrc` dargestellten Wert enthält, jedoch mit dem durch `vtNew` angegebenen Typ.  
  
 `pvarSrc`  
 in Ein Variant-Wert, der in einen neuen Typ geändert werden soll.  
  
 `lcid`  
 in Der Gebiets Schema Kontext, der beim wandeln der Argumente in oder aus Zeichen folgen verwendet werden soll.  
  
 `vtNew`  
 in Gibt den Typ an, für den `pvarDst` werden soll.  
  
## <a name="return-value"></a>Rückgabewert  
 Die Methode gibt ein `HRESULT` zurück. Mögliches Werte (aber nicht die Einzigen) sind die in der folgenden Tabelle.  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
  
## <a name="remarks"></a>Hinweise  
 Die `pvarDst`-und `pvarSrc` Argumente können gleich sein. in diesem Fall wird der ursprüngliche Wert überschrieben. Diese Methode übergibt `pvarDst` an die `VariantClear`-Funktion. Folglich sollte `pvarDst` mit einem gültigen Wert initialisiert werden.  
  
## <a name="see-also"></a>Siehe auch  
 [IVariantChangeType-Schnittstelle](../../winscript/reference/ivariantchangetype-interface.md)