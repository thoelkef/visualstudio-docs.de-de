---
title: IScriptNode::GetParent | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IScriptNode.GetParent
apilocation: scrobj.dll
helpviewer_keywords: IScriptNode::GetParent
ms.assetid: 0fb813f6-ab94-46b2-b0cf-ef5d1cd38ae4
caps.latest.revision: "7"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1da2f68de40a66b98b97ab7c7eb1d63748f1e07a
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="iscriptnodegetparent"></a>IScriptNode::GetParent
Gibt die `IScriptNode` -Objekt, das das übergeordnete Element eines Objekts ist.  
  
## <a name="syntax"></a>Syntax  
  
```  
HRESULT GetParent(  
   IScriptNode       **ppsnParent  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `ppsnParent`  
 [out] Die Adresse einer Variablen, die einen Zeiger auf empfängt die `IScriptNode` Schnittstelle der übergeordneten Instanz.  
  
 Wenn die Klasse implementiert `IScriptEntry` oder `IScriptScriptlet`, wird ein `IScriptNode` Objekt wird zurückgegeben.  
  
 Wenn die Klasse implementiert `IScriptNode` (eine Webseite, darstellt), wird NULL zurückgegeben.  
  
## <a name="return-value"></a>Rückgabewert  
 Eine `HRESULT`. Mögliches Werte (aber nicht die Einzigen) sind die in der folgenden Tabelle.  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
  
## <a name="remarks"></a>Hinweise  
  
## <a name="see-also"></a>Siehe auch  
 [IScriptNode-Schnittstelle](../../winscript/reference/iscriptnode-interface.md)