---
title: 'IScriptNode:: CreateChildEntry | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IScriptNode. CreateChildEntry
apilocation:
- scrobj.dll
helpviewer_keywords:
- IScriptNode::CreateChildEntry
ms.assetid: b9682505-4457-40e9-8691-235843637506
caps.latest.revision: 17
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8fcc010efe8fcf30a8f467dd94befff54bc5fac5
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
ms.locfileid: "24729690"
---
# <a name="iscriptnode-createchildentry"></a>IScriptNode::CreateChildEntry
Fügt eine untergeordnete Instanz `IScriptEntry`.  
  
## <a name="syntax"></a>Syntax  
  
```  
HRESULT CreateChildEntry(  
   ULONG              isn,  
   DWORD              dwCookie,  
   LPCOLESTR          pszDelimiter,  
   IScriptEntry       **ppse  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `isn`  
 [in] Der Index des untergeordneten Elements in der übergeordneten Tabelle.  
  
 `dwCookie`  
 [in] Ein Wert für die anwendungsdefinierte verwendet, das Hostobjekt, das die untergeordneten Eintrag zugeordnet werden soll.  
  
 `pszDelimiter`  
 [in] Die Adresse des Trennzeichens zum Ende der Skriptblock. Für die Analyse verwendet der Host in der Regel ein Trennzeichen (z. B. zwei einfache Anführungszeichen), um das Ende des Skriptblocks zu erkennen.  
  
 Das Trennzeichen kann das Skript, das Modul zum Bereitstellen der vorverarbeitung erstellen. Beispielsweise kann das Modul ein einfaches Anführungszeichen durch zwei einfache Anführungszeichen zur Verwendung als Trennzeichen ersetzen. Das Modul bestimmt, wie das Trennzeichen verwendet wird.  
  
 Auf NULL festgelegt, wenn ein Trennzeichen nicht das Ende des Skriptblocks markieren.  
  
 `ppse`  
 [out] Die Adresse einer Variablen, die einen Zeiger auf empfängt die `IScriptEntry` Schnittstelle der untergeordneten Instanz.  
  
 Für `IScriptNode` Objekte, die eine Webseite darstellen, gibt dieser Parameter eine `IScriptEntry` Instanz, die einen Skriptblock angibt.  
  
 Für `IScriptEntry` Objekte, die einen Skriptblock darstellen, gibt dieser Parameter eine `IScriptEntry` Instanz, der ein Funktionsobjekt angibt.  
  
 Für `IScriptEntry` Objekte, die eine Funktion darstellen-Objekt, diese Methode ein Fehler auftritt.  
  
 Für `IScriptScriptlet` Objekte aufweist, diese Methode ein Fehler auftritt.  
  
## <a name="return-value"></a>Rückgabewert  
 Eine `HRESULT`. Mögliches Werte (aber nicht die Einzigen) sind die in der folgenden Tabelle.  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
  
## <a name="remarks"></a>Hinweise  
 Die `IScriptNode` Schnittstelle darstellt, einer Webseite oder seiner Elemente. Die `IScriptEntry` Schnittstelle (abgeleitet von `IScriptNode`) entweder ein Skriptblock oder ein Funktionsobjekt darstellt. Die `IScriptScriptlet` Schnittstelle (abgeleitet von `IScriptEntry`) stellt einen Ereignishandler dar.  
  
## <a name="see-also"></a>Siehe auch  
 [IScriptNode-Schnittstelle](../../winscript/reference/iscriptnode-interface.md)   
 [IScriptEntry-Schnittstelle](../../winscript/reference/iscriptentry-interface.md)