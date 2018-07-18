---
title: IScriptNode::CreateChildHandler | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: ff2ba40d1570e23f0256bd34ca8aff0f8d77ce5c
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
ms.locfileid: "24729560"
---
# <a name="iscriptnodecreatechildhandler"></a>IScriptNode::CreateChildHandler
Fügt eine Scriptlet als untergeordnete Instanz von einem `IScriptNode`.  
  
## <a name="syntax"></a>Syntax  
  
```  
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
 [in Size_is (`cpszNames`)] eine Liste der Bezeichner nicht mit dem vollqualifizierten Namen auf dem Host.  
  
 `cpszNames`  
 [in] Die Anzahl der IDs in der `prgpszNames` Parameter.  
  
 `pszEvent`  
 [in] Der Pufferadresse, die den Ereignisnamen, die dem Scriptlet zugeordnet angibt.  
  
 `pszDelimiter`  
 [in] Die Adresse des Trennzeichens zum Ende der Skriptblock. Für die Analyse verwendet der Host in der Regel ein Trennzeichen (z. B. zwei einfache Anführungszeichen), um das Ende des Skriptblocks zu erkennen.  
  
 Das Trennzeichen kann unter Verwendung des Skripts authoring Modul vorverarbeitung. Beispielsweise kann das Modul ein einfaches Anführungszeichen durch zwei einfache Anführungszeichen zur Verwendung als Trennzeichen ersetzen. Das Modul bestimmt, wie das Trennzeichen verwendet wird.  
  
 Auf NULL festgelegt, wenn kein Trennzeichen verwendet wird, um das Ende der Skriptblock zu identifizieren.  
  
 `ptiSignature`  
 [in] Die Typinformationen für ein Funktionsobjekt.  
  
 `iMethodSignature`  
 [in] Der Index der Funktion in der `ITypeInfo``ptiSignature` Parameter.  
  
 `isn`  
 [in] Der Index des untergeordneten Elements in der übergeordneten Tabelle.  
  
 `dwCookie`  
 [in] Ein anwendungsdefinierten Wert, der verwendet wird, das Hostobjekt, das den Eintrag zugeordnet werden soll.  
  
 `ppse`  
 [out] Die Adresse einer Variablen, die einen Zeiger auf empfängt die `IScriptEntry` Schnittstelle der untergeordneten Instanz.  
  
## <a name="return-value"></a>Rückgabewert  
 Eine `HRESULT`. Mögliches Werte (aber nicht die Einzigen) sind die in der folgenden Tabelle.  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
  
## <a name="remarks"></a>Hinweise  
 Scriptlet gibt einen Ereignishandler. Diese Methode erstellt eine Scriptlet aus, wenn sie aufgerufen wird, indem Sie ein `IScriptNode` Objekt, das eine Webseite darstellt. Diese Methode kann nicht ausgeführt werden, wenn er von anderen Schnittstellen aufgerufen wird.  
  
## <a name="see-also"></a>Siehe auch  
 [IScriptNode-Schnittstelle](../../winscript/reference/iscriptnode-interface.md)   
 [IScriptEntry-Schnittstelle](../../winscript/reference/iscriptentry-interface.md)