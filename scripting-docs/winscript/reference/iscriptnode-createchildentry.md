---
title: 'IScriptNode:: CreateChildEntry | Microsoft-Dokumentation'
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
ms.openlocfilehash: a8ca4ab504a9da2a63d5c70330d50e2c97e09817
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/08/2019
ms.locfileid: "54088230"
---
# <a name="iscriptnode-createchildentry"></a>IScriptNode:: CreateChildEntry
Fügt eine untergeordnete Instanz `IScriptEntry`.  
  
## <a name="syntax"></a>Syntax  
  
```cpp
HRESULT CreateChildEntry(  
   ULONG              isn,  
   DWORD              dwCookie,  
   LPCOLESTR          pszDelimiter,  
   IScriptEntry       **ppse  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `isn`  
 [in] Der Index des untergeordneten Elements im übergeordneten Element.  
  
 `dwCookie`  
 [in] Einer der Anwendung definierter Wert verwendet, das Hostobjekt, das die untergeordneten Eintrag zugeordnet werden soll.  
  
 `pszDelimiter`  
 [in] Die Adresse des Trennzeichens Ende-des-Skript-Block. Für die Analyse verwendet der Host in der Regel ein Trennzeichen (z. B. zwei einfache Anführungszeichen), um das Ende des Skriptblocks zu erkennen.  
  
 Das Trennzeichen kann das Skript-Engine zum Bereitstellen der vorverarbeitung zu erstellen. Beispielsweise kann die Engine ein einfaches Anführungszeichen durch zwei einfache Anführungszeichen für die Verwendung als Trennzeichen ersetzen. Die Engine bestimmt, wie das Trennzeichen verwendet wird.  
  
 Auf NULL festgelegt, wenn ein Trennzeichen nicht das Ende des Skriptblocks markiert.  
  
 `ppse`  
 [out] Die Adresse einer Variablen, die einen Zeiger auf empfängt die `IScriptEntry` Schnittstelle die untergeordnete Instanz.  
  
 Für `IScriptNode` Objekte, die eine Webseite darstellen, gibt dieser Parameter ein `IScriptEntry` Instanz, die einen Skriptblock angibt.  
  
 Für `IScriptEntry` darstellende – Objekte einen Skriptblock, gibt dieser Parameter ein `IScriptEntry` -Instanz, ein Funktionsobjekt angibt.  
  
 Für `IScriptEntry` eine Funktion darstellende – Objekte Objekt, das diese Methode schlägt fehl.  
  
 Für `IScriptScriptlet` Objekten, die diese Methode schlägt fehl.  
  
## <a name="return-value"></a>Rückgabewert  
 Eine `HRESULT`. Mögliches Werte (aber nicht die Einzigen) sind die in der folgenden Tabelle.  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
  
## <a name="remarks"></a>Hinweise  
 Die `IScriptNode` Schnittstelle darstellt, einer Webseite oder seiner Elemente. Die `IScriptEntry` Schnittstelle (abgeleitet von `IScriptNode`) stellt entweder ein Skriptblock oder ein Funktionsobjekt. Die `IScriptScriptlet` Schnittstelle (abgeleitet von `IScriptEntry`) stellt einen Ereignishandler dar.  
  
## <a name="see-also"></a>Siehe auch  
 [IScriptNode-Schnittstelle](../../winscript/reference/iscriptnode-interface.md)   
 [IScriptEntry-Schnittstelle](../../winscript/reference/iscriptentry-interface.md)