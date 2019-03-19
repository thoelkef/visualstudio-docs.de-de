---
title: IScriptNode::CreateChildHandler | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IScriptNode.CreateChildHandler
apilocation:
- scrobj.dll
helpviewer_keywords:
- IScriptNode::CreateChildHandler
ms.assetid: 4ce5eb10-1a3f-43b0-a4b7-599a397ed3a2
caps.latest.revision: 14
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: bca8b30021d39638f3755bace2625bb38a44242d
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/19/2019
ms.locfileid: "58149246"
---
# <a name="iscriptnodecreatechildhandler"></a>IScriptNode::CreateChildHandler
Fügt eine Scriptlet als untergeordnete Instanz von einem `IScriptNode`.  
  
## <a name="syntax"></a>Syntax  
  
```cpp
HRESULT CreateChildHandler(  
   LPCOLESTR          pszDefaultName,  
   LPCOLESTR          *prgpszNames,  
   ULONG              cpszNames,  
   LPCOLESTR          pszEvent,  
   LPCOLESTR          pszDelimiter,  
   ITypeInfo*         ptiSignature,  
   ULONG              iMethodSignature,  
   ULONG              isn,  
   DWORD              dwCookie,  
   IScriptEntry       **ppse  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pszDefaultName`  
 [in] Die Adresse der Standardname des Scriptlets zugeordnet werden soll.  
  
 `prgpszNames`  
 [in, Size_is (`cpszNames`)] eine Liste mit IDs aus dem vollqualifizierten Namen auf dem Host.  
  
 `cpszNames`  
 [in] Die Anzahl von Bezeichnern in die `prgpszNames` Parameter.  
  
 `pszEvent`  
 [in] Der Pufferadresse, die den Ereignisnamen, die dem Scriptlet zugeordnet identifiziert.  
  
 `pszDelimiter`  
 [in] Die Adresse des Trennzeichens Ende-des-Skript-Block. Für die Analyse verwendet der Host in der Regel ein Trennzeichen (z. B. zwei einfache Anführungszeichen), um das Ende des Skriptblocks zu erkennen.  
  
 Das Trennzeichen ermöglicht vorverarbeitung von dem Skript-Engine-Erstellung. Beispielsweise kann die Engine ein einfaches Anführungszeichen durch zwei einfache Anführungszeichen für die Verwendung als Trennzeichen ersetzen. Die Engine bestimmt, wie das Trennzeichen verwendet wird.  
  
 Auf NULL festgelegt, wenn kein Trennzeichen verwendet wird, um das Ende der Skriptblock zu identifizieren.  
  
 `ptiSignature`  
 [in] Die Typinformationen für ein Funktionsobjekt.  
  
 `iMethodSignature`  
 [in] Der Index der Funktion in der `ITypeInfo``ptiSignature` Parameter.  
  
 `isn`  
 [in] Der Index des untergeordneten Elements im übergeordneten Element.  
  
 `dwCookie`  
 [in] Eine Anwendung definierte Wert, der verwendet wird, das Hostobjekt, das den Eintrag zugeordnet werden soll.  
  
 `ppse`  
 [out] Die Adresse einer Variablen, die einen Zeiger auf empfängt die `IScriptEntry` Schnittstelle die untergeordnete Instanz.  
  
## <a name="return-value"></a>Rückgabewert  
 Eine `HRESULT`. Mögliches Werte (aber nicht die Einzigen) sind die in der folgenden Tabelle.  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
  
## <a name="remarks"></a>Hinweise  
 Scriptlet gibt einen Ereignishandler an. Diese Methode erstellt eine Scriptlet aus, wenn sie, indem aufgerufen wird ein `IScriptNode` -Objekt, eine Webseite darstellt. Diese Methode ist nicht erfolgreich, wenn sie über andere Schnittstellen aufgerufen wird.  
  
## <a name="see-also"></a>Siehe auch  
 [IScriptNode-Schnittstelle](../../winscript/reference/iscriptnode-interface.md)   
 [IScriptEntry-Schnittstelle](../../winscript/reference/iscriptentry-interface.md)