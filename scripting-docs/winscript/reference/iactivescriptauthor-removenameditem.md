---
title: 'Iactivescriptauthor:: RemoveNamedItem | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptAuthor.RemoveNamedItem
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptAuthor::RemoveNamedItem
ms.assetid: 1173ef46-39a5-4bc1-8e0c-89259a16be16
caps.latest.revision: 14
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: cade532d2ca276237981855cafe12804307d0bb6
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572844"
---
# <a name="iactivescriptauthorremovenameditem"></a>IActiveScriptAuthor::RemoveNamedItem
Entfernt ein `NamedItem` Objekt aus dem Namespace der Skript Erstellungs-Engine.  
  
## <a name="syntax"></a>Syntax  
  
```cpp
HRESULT RemoveNamedItem(  
   LPCOLESTR          pszName  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pszName`  
 in Die Adresse des Puffers, der das zu entfernenden `NamedItem` Objekt identifiziert.  
  
## <a name="return-value"></a>Rückgabewert  
 Eine `HRESULT`. Mögliches Werte (aber nicht die Einzigen) sind die in der folgenden Tabelle.  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
|`S_FALSE`|Das `NamedItem`-Objekt ist nicht im Namespace der Skript Erstellungs-Engine vorhanden.|  
  
## <a name="remarks"></a>Hinweise  
 [IActiveScript:: addnameditem](../../winscript/reference/iactivescript-addnameditem.md) wird zum Einfügen des `NamedItem` Objekts in den Namespace der Skript Erstellungs-Engine verwendet.  
  
## <a name="see-also"></a>Siehe auch  
 [Iactivescriptauthor-Schnittstelle](../../winscript/reference/iactivescriptauthor-interface.md)    
 [IActiveScriptAuthor::AddNamedItem](../../winscript/reference/iactivescriptauthor-addnameditem.md)