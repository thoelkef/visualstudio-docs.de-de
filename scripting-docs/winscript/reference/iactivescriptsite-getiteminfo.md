---
title: 'Iactivescriptsite:: getiteminfo | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptSite.GetItemInfo
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptSite_GetItemInfo
ms.assetid: f859ed3b-02c1-4924-99f8-5f5bf1bf8405
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3c0458f42466a264c30a440b1b14a028a2457f12
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/18/2019
ms.locfileid: "72570926"
---
# <a name="iactivescriptsitegetiteminfo"></a>IActiveScriptSite::GetItemInfo
Ermöglicht der Skript-Engine das Abrufen von Informationen zu einem Element, das mit der [IActiveScript:: addnameditem](../../winscript/reference/iactivescript-addnameditem.md) -Methode hinzugefügt wurde.  
  
## <a name="syntax"></a>Syntax  
  
```cpp
HRESULT GetItemInfo(  
    LPCOLESTR pstrName,     // address of item name  
    DWORD dwReturnMask,     // bit mask for information retrieval  
    IUnknown **ppunkItem,   // address of pointer to item's IUnknown  
    ITypeInfo **ppTypeInfo  // address of pointer to item's ITypeInfo  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pstrName`  
 in Der Name, der dem Element zugeordnet ist, wie in der [IActiveScript:: addnameditem](../../winscript/reference/iactivescript-addnameditem.md) -Methode angegeben.  
  
 `dwReturnMask`  
 in Eine Bitmaske, die angibt, welche Informationen über das Element zurückgegeben werden sollen. Die Skript-Engine sollte die minimale Menge an Informationen anfordern, da einige der Rückgabe Parameter (z. b. `ITypeInfo`) viel Zeit zum Laden oder generieren benötigen. Kann eine Kombination der folgenden Werte sein:  
  
|Wert|Bedeutung|  
|-----------|-------------|  
|SCRIPTINFO_IUNKNOWN|Gibt die `IUnknown`-Schnittstelle für dieses Element zurück.|  
|SCRIPTINFO_ITYPEINFO|Gibt die `ITypeInfo`-Schnittstelle für dieses Element zurück.|  
  
 `ppunkItem`  
 vorgenommen Adresse einer Variablen, die einen Zeiger auf die `IUnknown`-Schnittstelle empfängt, die dem angegebenen Element zugeordnet ist. Die Skript-Engine kann die `IUnknown::QueryInterface`-Methode verwenden, um die `IDispatch`-Schnittstelle für das Element abzurufen. Dieser Parameter empfängt NULL, wenn `dwReturnMask` den SCRIPTINFO_IUNKNOWN-Wert nicht enthält. Außerdem wird NULL empfangen, wenn dem Elementnamen kein Objekt zugeordnet ist. Dieser Mechanismus wird zum Erstellen einer einfachen Klasse verwendet, wenn das benannte Element mit dem SCRIPTITEM_CODEONLY-Flag hinzugefügt wurde, das in der [IActiveScript:: addnameditem](../../winscript/reference/iactivescript-addnameditem.md) -Methode festgelegt wurde.  
  
 `ppTypeInfo`  
 vorgenommen Adresse einer Variablen, die einen Zeiger auf die `ITypeInfo`-Schnittstelle empfängt, die dem Element zugeordnet ist. Dieser Parameter empfängt NULL, wenn `dwReturnMask` den SCRIPTINFO_ITYPEINFO-Wert nicht enthält oder wenn keine Typinformationen für dieses Element verfügbar sind. Wenn keine Typinformationen verfügbar sind, kann das Objekt keine Ereignisse als Quelle aufweisen, und die namens Bindung muss mit der `IDispatch::GetIDsOfNames`-Methode realisiert werden. Beachten Sie, dass die `ITypeInfo`-Schnittstelle die Co-Klasse des Elements (TKIND_COCLASS) beschreibt, da das Objekt möglicherweise mehrere Schnittstellen und Ereignis Schnittstellen unterstützt. Wenn das Element die `IProvideMultipleTypeInfo`-Schnittstelle unterstützt, entspricht die abgerufene `ITypeInfo` Schnittstelle dem Index NULL-`ITypeInfo`, der mithilfe der `IProvideMultipleTypeInfo::GetInfoOfIndex`-Methode abgerufen wird.  
  
## <a name="return-value"></a>Rückgabewert  
 Gibt einen der folgenden Werte zurück:  
  
|Rückgabewert|Bedeutung|  
|------------------|-------------|  
|`S_OK`|Erfolgreich.|  
|`E_INVALIDARG`|Ein Argument war ungültig.|  
|`E_POINTER`|Es wurde ein ungültiger Zeiger angegeben.|  
|`TYPE_E_ELEMENTNOTFOUND`|Ein Element mit dem angegebenen Namen wurde nicht gefunden.|  
  
## <a name="remarks"></a>Hinweise  
 Diese Methode ruft nur die Informationen ab, die vom `dwReturnMask`-Parameter angegeben werden. Dadurch wird die Leistung verbessert. Wenn z. b. eine `ITypeInfo`-Schnittstelle für ein Element nicht benötigt wird, wird Sie in `dwReturnMask` nicht angegeben.  
  
## <a name="see-also"></a>Siehe auch  
 [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md)