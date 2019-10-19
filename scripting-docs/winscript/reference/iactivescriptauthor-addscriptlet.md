---
title: 'Iactivescriptauthor:: addscriptlet | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptAuthor.AddScriptlet
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptAuthor::AddScriptlet
ms.assetid: 879a6651-f187-4934-b130-c1247549900b
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3a349a848f282e6b3a228c7b17009e0261801be5
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/18/2019
ms.locfileid: "72577975"
---
# <a name="iactivescriptauthoraddscriptlet"></a>IActiveScriptAuthor::AddScriptlet
Fügt ein Code-Scriptlet als untergeordnetes Element der Stamm Ebene `IScriptNode`-Objekts hinzu. Auf dem Host darf der voll qualifizierte Name des Scriptlets nur zwei Ebenen aufweisen.  
  
## <a name="syntax"></a>Syntax  
  
```cpp
HRESULT AddScriptlet(  
   LPCOLESTR pszDefaultName,  
   LPCOLESTR pszCode,  
   LPCOLESTR pszItemName,  
   LPCOLESTR pszSubItemName,  
   LPCOLESTR pszEventName,  
   LPCOLESTR pszDelimiter,  
   DWORD dwCookie,  
   DWORD dwFlags  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pszDefaultName`  
 in Die Adresse des Standard namens, der dem Scriptlet zugeordnet werden soll.  
  
 `pszCode`  
 in Die Adresse des Scriptlet-Texts.  
  
 `pszItemName`  
 in Die Puffer Adresse des Bezeichner der obersten Ebene des voll qualifizierten Scriptlet-namens im Host.  
  
 `pszSubItemName`  
 in Die Puffer Adresse des Bezeichners der zweiten Ebene des voll qualifizierten Scriptlet-namens im Host. Auf NULL festgelegt, wenn der Name nur eine Ebene aufweist.  
  
 `pszEventName`  
 in Die Adresse eines Puffers, der den Ereignis Namen enthält, für den das Scriptlet ein Ereignishandler ist.  
  
 `pszDelimiter`  
 in Die Adresse des Trenn Zeichens für das Ende des Skript Blocks. Wenn `pszCode` aus einem Stream von Text analysiert wird, verwendet der Host normalerweise ein Trennzeichen (z. b. zwei einfache Anführungszeichen), um das Ende des Skript Blocks zu erkennen. Legen Sie diesen Parameter auf NULL fest, wenn ein Trennzeichen das Ende des Skript Blocks nicht markiert.  
  
 `dwCookie`  
 in Ein von der Anwendung definierter Wert, der verwendet wird, um das Scriptlet einem Host Objekt zuzuordnen.  
  
 `dwFlags`  
 in Nicht verwendet.  
  
## <a name="return-value"></a>Rückgabewert  
 Eine `HRESULT`. Mögliches Werte (aber nicht die Einzigen) sind die in der folgenden Tabelle.  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
  
## <a name="remarks"></a>Hinweise  
  
## <a name="see-also"></a>Siehe auch  
 [IActiveScriptAuthor-Schnittstelle](../../winscript/reference/iactivescriptauthor-interface.md)