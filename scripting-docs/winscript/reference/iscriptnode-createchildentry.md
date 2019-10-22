---
title: 'Iscriptnode:: kreatechildentry | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 01/18/2017
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
ms.openlocfilehash: c58ff83c43a1418e6fb7bd8945afa181af60c68a
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/18/2019
ms.locfileid: "72573616"
---
# <a name="iscriptnode-createchildentry"></a>IScriptNode::CreateChildEntry
Fügt eine untergeordnete Instanz von `IScriptEntry` hinzu.  
  
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
 in Der Index des untergeordneten Elements in der übergeordneten.  
  
 `dwCookie`  
 in Ein von der Anwendung definierter Wert, der verwendet wird, um den untergeordneten Eintrag dem Host Objekt zuzuordnen.  
  
 `pszDelimiter`  
 in Die Adresse des Trenn Zeichens für das Ende des Skript Blocks. Zum Auswerten verwendet der Host normalerweise ein Trennzeichen (z. b. zwei einfache Anführungszeichen), um das Ende des Skript Blocks zu erkennen.  
  
 Das Trennzeichen ermöglicht der Skript Erstellungs-Engine, eine Vorverarbeitung bereitzustellen. Beispielsweise kann die Engine ein einzelnes Anführungszeichen durch zwei einfache Anführungszeichen ersetzen, die als Trennzeichen verwendet werden sollen. Die Engine bestimmt, wie das Trennzeichen verwendet wird.  
  
 Auf NULL festgelegt, wenn ein Trennzeichen das Ende des Skript Blocks nicht markiert.  
  
 `ppse`  
 vorgenommen Die Adresse einer Variablen, die einen Zeiger auf die `IScriptEntry`-Schnittstelle der untergeordneten Instanz empfängt.  
  
 Bei `IScriptNode` Objekten, die eine Webseite darstellen, gibt dieser Parameter eine `IScriptEntry` Instanz zurück, die einen Skriptblock angibt.  
  
 Bei `IScriptEntry` Objekten, die einen Skriptblock darstellen, gibt dieser Parameter eine `IScriptEntry` Instanz zurück, die ein Funktions Objekt angibt.  
  
 Bei `IScriptEntry` Objekten, die ein Funktions Objekt darstellen, schlägt diese Methode fehl.  
  
 Bei `IScriptScriptlet`-Objekten schlägt diese Methode fehl.  
  
## <a name="return-value"></a>Rückgabewert  
 Eine `HRESULT`. Mögliches Werte (aber nicht die Einzigen) sind die in der folgenden Tabelle.  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
  
## <a name="remarks"></a>Hinweise  
 Die `IScriptNode`-Schnittstelle stellt eine Webseite oder deren Elemente dar. Die `IScriptEntry`-Schnittstelle (die von `IScriptNode` abgeleitet ist) stellt entweder einen Skriptblock oder ein Funktions Objekt dar. Die `IScriptScriptlet`-Schnittstelle (die von `IScriptEntry` abgeleitet ist) stellt einen Ereignishandler dar.  
  
## <a name="see-also"></a>Siehe auch  
 [Iscriptnode-Schnittstelle](../../winscript/reference/iscriptnode-interface.md)    
 [IScriptEntry-Schnittstelle](../../winscript/reference/iscriptentry-interface.md)