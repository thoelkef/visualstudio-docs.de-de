---
title: IVariantChangeType::ChangeType | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IVariantChangeType.ChangeType
apilocation: scrobj.dll
helpviewer_keywords: IVariantChangeType::ChangeType
ms.assetid: 52374764-c42e-49af-a219-ee00c535a118
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d742d1bd57c85aa75c9ccd60479d08c1a559fb37
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="ivariantchangetypechangetype"></a>IVariantChangeType::ChangeType
Akzeptiert einen Varianten-Wert, und erstellt eine neue Variante mit einem angegebenen Typ.  
  
## <a name="syntax"></a>Syntax  
  
```  
HRESULT ChangeType(  
   VARIANT*  pvarDst,  
   VARIANT*  pvarSrc,  
   LCID  lcid,  
   VARTYPE  vtNew  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pvarDst`  
 [in, out] Eine Variante der dargestellte Wert enthalten `pvarSrc`, jedoch mit den vom angegebenen Typ `vtNew`.  
  
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
 Die `pvarDst` und `pvarSrc` Argumente möglicherweise gleich sind, und in diesem Fall wird der ursprüngliche Wert überschrieben. Diese Methode transferiert `pvarDst` auf die `VariantClear` -Funktion, und infolgedessen wird auch `pvarDst` sollte auf einen gültigen Wert initialisiert werden.  
  
## <a name="see-also"></a>Siehe auch  
 [IVariantChangeType-Schnittstelle](../../winscript/reference/ivariantchangetype-interface.md)