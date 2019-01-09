---
title: IActiveScriptAuthor::RemoveNamedItem | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: 64f62acd02e0901af341a571fb09ba81f3a11f28
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/08/2019
ms.locfileid: "54088828"
---
# <a name="iactivescriptauthorremovenameditem"></a>IActiveScriptAuthor::RemoveNamedItem
Entfernt eine `NamedItem` Objekt aus dem Namespace, der das Skript-Engine-Erstellung.  
  
## <a name="syntax"></a>Syntax  
  
```cpp
HRESULT RemoveNamedItem(  
   LPCOLESTR          pszName  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pszName`  
 [in] Die Adresse des Puffers, der identifiziert die `NamedItem` zu entfernende Objekt.  
  
## <a name="return-value"></a>Rückgabewert  
 Eine `HRESULT`. Mögliches Werte (aber nicht die Einzigen) sind die in der folgenden Tabelle.  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
|`S_FALSE`|Die `NamedItem` Objekt ist nicht vorhanden ist, im Namespace des Skript-Engine-Erstellung.|  
  
## <a name="remarks"></a>Hinweise  
 [Addnameditem](../../winscript/reference/iactivescript-addnameditem.md) wird verwendet, um das Einfügen der `NamedItem` Objekt in das Skript-Engine-Namespace erstellen.  
  
## <a name="see-also"></a>Siehe auch  
 [IActiveScriptAuthor-Schnittstelle](../../winscript/reference/iactivescriptauthor-interface.md)   
 [IActiveScriptAuthor::AddNamedItem](../../winscript/reference/iactivescriptauthor-addnameditem.md)