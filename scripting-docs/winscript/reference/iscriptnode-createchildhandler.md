---
title: 'Iscriptnode:: kreatechildhandler | Microsoft-Dokumentation'
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
ms.openlocfilehash: 9e024bb7d6a81b35994edddfe9e71666b0ee8df0
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/18/2019
ms.locfileid: "72573600"
---
# <a name="iscriptnodecreatechildhandler"></a>IScriptNode::CreateChildHandler
Fügt ein Scriptlet als untergeordnete Instanz eines `IScriptNode` hinzu.  
  
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
 in Die Adresse des Standard namens, der dem Scriptlet zugeordnet werden soll.  
  
 `prgpszNames`  
 [in, size_is (`cpszNames`)] Eine Liste der Bezeichner aus dem voll qualifizierten Namen auf dem Host.  
  
 `cpszNames`  
 in Die Anzahl der Bezeichner im `prgpszNames`-Parameter.  
  
 `pszEvent`  
 in Die Puffer Adresse, die den dem Scriptlet zugeordneten Ereignis Namen identifiziert.  
  
 `pszDelimiter`  
 in Die Adresse des Trenn Zeichens für das Ende des Skript Blocks. Zum Auswerten verwendet der Host normalerweise ein Trennzeichen (z. b. zwei einfache Anführungszeichen), um das Ende des Skript Blocks zu erkennen.  
  
 Das Trennzeichen ermöglicht die Vorverarbeitung durch das Skript Erstellungs Modul. Beispielsweise kann die Engine ein einzelnes Anführungszeichen durch zwei einfache Anführungszeichen ersetzen, die als Trennzeichen verwendet werden sollen. Die Engine bestimmt, wie das Trennzeichen verwendet wird.  
  
 Auf NULL festgelegt, wenn kein Trennzeichen verwendet wird, um das Ende des Skript Blocks zu identifizieren.  
  
 `ptiSignature`  
 in Die Typinformationen für ein Funktions Objekt.  
  
 `iMethodSignature`  
 in Der Index der Funktion im `ITypeInfo``ptiSignature`-Parameter.  
  
 `isn`  
 in Der Index des untergeordneten Elements in der übergeordneten.  
  
 `dwCookie`  
 in Ein von der Anwendung definierter Wert, der verwendet wird, um den Eintrag dem Host Objekt zuzuordnen.  
  
 `ppse`  
 vorgenommen Die Adresse einer Variablen, die einen Zeiger auf die `IScriptEntry`-Schnittstelle der untergeordneten Instanz empfängt.  
  
## <a name="return-value"></a>Rückgabewert  
 Eine `HRESULT`. Mögliches Werte (aber nicht die Einzigen) sind die in der folgenden Tabelle.  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
  
## <a name="remarks"></a>Hinweise  
 Ein Scriptlet gibt einen Ereignishandler an. Diese Methode erstellt ein Scriptlet, wenn Sie von einem `IScriptNode`-Objekt aufgerufen wird, das eine Webseite darstellt. Diese Methode ist nicht erfolgreich, wenn Sie von anderen Schnittstellen aufgerufen wird.  
  
## <a name="see-also"></a>Siehe auch  
 [Iscriptnode-Schnittstelle](../../winscript/reference/iscriptnode-interface.md)    
 [IScriptEntry-Schnittstelle](../../winscript/reference/iscriptentry-interface.md)