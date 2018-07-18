---
title: IActiveScriptSite::GetItemInfo | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: ccb898c14571d1f1fd1fcae7cb0b9a6d322f2754
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
ms.locfileid: "24725420"
---
# <a name="iactivescriptsitegetiteminfo"></a>IActiveScriptSite::GetItemInfo
Ermöglicht das Skriptmodul zum Abrufen von Informationen zu einem Element hinzugefügt, mit der [IActiveScript::AddNamedItem](../../winscript/reference/iactivescript-addnameditem.md) Methode.  
  
## <a name="syntax"></a>Syntax  
  
```  
HRESULT GetItemInfo(  
    LPCOLESTR pstrName,     // address of item name  
    DWORD dwReturnMask,     // bit mask for information retrieval  
    IUnknown **ppunkItem,   // address of pointer to item's IUnknown  
    ITypeInfo **ppTypeInfo  // address of pointer to item's ITypeInfo  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pstrName`  
 [in] Das Element, entsprechend den Angaben in zugeordnete Name der [IActiveScript::AddNamedItem](../../winscript/reference/iactivescript-addnameditem.md) Methode.  
  
 `dwReturnMask`  
 [in] Eine Bitmaske, die angeben, welche Informationen über das Element zurückgegeben werden soll. Das Skriptmodul sollte mindestens ein Videospeicher von Informationen möglich anfordern, da einige der Rückgabeparameter (z. B. `ITypeInfo`) dauert sehr viel Zeit zum Laden oder zu generieren. Eine Kombination der folgenden Werte ist möglich:  
  
|Wert|Bedeutung|  
|-----------|-------------|  
|SCRIPTINFO_IUNKNOWN|Gibt die `IUnknown` Schnittstelle für dieses Element.|  
|SCRIPTINFO_ITYPEINFO|Gibt die `ITypeInfo` Schnittstelle für dieses Element.|  
  
 `ppunkItem`  
 [out] Adresse einer Variablen, die einen Zeiger auf empfängt die `IUnknown` Schnittstelle, die dem angegebenen Element zugeordnet sind. Das Skriptmodul können die `IUnknown::QueryInterface` Methode zum Abrufen der `IDispatch` Schnittstelle für das Element. Dieser Parameter NULL empfängt, wenn `dwReturnMask` schließt nicht den SCRIPTINFO_IUNKNOWN-Wert. Darüber hinaus erhält sie NULL, wenn kein Objekt, das den Namen des Elements zugeordnet ist; Dieser Mechanismus wird verwendet, um eine einfache Klasse zu erstellen, wenn das benannte Element, mit dem SCRIPTITEM_CODEONLY-Flag festgelegt hinzugefügt wurde, der [IActiveScript::AddNamedItem](../../winscript/reference/iactivescript-addnameditem.md) Methode.  
  
 `ppTypeInfo`  
 [out] Adresse einer Variablen, die einen Zeiger auf empfängt die `ITypeInfo` Schnittstelle, die dem Element zugeordnet. Dieser Parameter NULL empfängt, wenn `dwReturnMask` schließt nicht den Wert SCRIPTINFO_ITYPEINFO oder ob Typinformationen nicht verfügbar für dieses Element ist. Wenn Typinformationen nicht verfügbar ist, das Objekt kann nicht Ereignissen der Datenquelle und namensbindung muss realisiert werden, mit der `IDispatch::GetIDsOfNames` Methode. Beachten Sie, dass die `ITypeInfo` Schnittstelle abgerufen beschreibt die Element-Co-Klasse (TKIND_COCLASS), da das Objekt mehrere Schnittstellen und Ereignisschnittstellen unterstützen kann. Wenn das Element unterstützt die `IProvideMultipleTypeInfo` -Schnittstelle, die `ITypeInfo` Schnittstelle abgerufen ist identisch mit dem Index 0 (null) `ITypeInfo` , würde mit abgerufen werden die `IProvideMultipleTypeInfo::GetInfoOfIndex` Methode.  
  
## <a name="return-value"></a>Rückgabewert  
 Gibt einen der folgenden Werte zurück:  
  
|Rückgabewert|Bedeutung|  
|------------------|-------------|  
|`S_OK`|Erfolgreich.|  
|`E_INVALIDARG`|Ein Argument war ungültig.|  
|`E_POINTER`|Es wurde ein ungültiger Zeiger angegeben.|  
|`TYPE_E_ELEMENTNOTFOUND`|Ein Element mit dem angegebenen Namen wurde nicht gefunden.|  
  
## <a name="remarks"></a>Hinweise  
 Diese Methode ruft nur die Informationen, die vom angegebenen ab der `dwReturnMask` Parameter; Dies verbessert die Leistung. Z. B. wenn ein `ITypeInfo` Schnittstelle nicht für ein Element erforderlich ist, einfach nicht angegeben ist im `dwReturnMask`.  
  
## <a name="see-also"></a>Siehe auch  
 [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md)