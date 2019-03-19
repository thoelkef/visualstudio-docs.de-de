---
title: 'Iactivescriptsite:: GetItemInfo | Microsoft-Dokumentation'
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
ms.openlocfilehash: 997245f8e4fd43ac2162587f07e4c8711af7caac
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/19/2019
ms.locfileid: "58148684"
---
# <a name="iactivescriptsitegetiteminfo"></a>IActiveScriptSite::GetItemInfo
Ermöglicht die Skript-Engine zum Abrufen von Informationen zu einem Element hinzugefügt, mit der [Addnameditem](../../winscript/reference/iactivescript-addnameditem.md) Methode.  
  
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
 [in] Das Element, wie angegeben in zugeordnete Name der [Addnameditem](../../winscript/reference/iactivescript-addnameditem.md) Methode.  
  
 `dwReturnMask`  
 [in] Eine Bitmaske, die angeben, welche Informationen über das Element zurückgegeben werden sollen. Die Skript-Engine sollten die Mindestmenge an Informationen anfordern, da einige der-Parametern (z. B. `ITypeInfo`) dauert sehr viel Zeit zum Laden oder zu generieren. Eine Kombination der folgenden Werte sind möglich:  
  
|Wert|Bedeutung|  
|-----------|-------------|  
|SCRIPTINFO_IUNKNOWN|Gibt die `IUnknown` Schnittstelle für dieses Element.|  
|SCRIPTINFO_ITYPEINFO|Gibt die `ITypeInfo` Schnittstelle für dieses Element.|  
  
 `ppunkItem`  
 [out] Adresse einer Variablen, die einen Zeiger auf empfängt die `IUnknown` Schnittstelle, die dem angegebenen Element zugeordnet. Die Skript-Engine können die `IUnknown::QueryInterface` Methode zum Abrufen der `IDispatch` Schnittstelle für das Element. Dieser Parameter NULL empfängt, wenn `dwReturnMask` umfasst nicht den SCRIPTINFO_IUNKNOWN-Wert. Darüber hinaus empfängt es NULL, wenn kein Objekt, das den Namen des Elements zugeordnet ist; Dieser Mechanismus wird verwendet, um eine einfache Klasse erstellt, wenn Sie der Namen des Elements mit festgelegtem SCRIPTITEM_CODEONLY-Flag hinzugefügt wurde die [Addnameditem](../../winscript/reference/iactivescript-addnameditem.md) Methode.  
  
 `ppTypeInfo`  
 [out] Adresse einer Variablen, die einen Zeiger auf empfängt die `ITypeInfo` Schnittstelle, die dem Element zugeordnet. Dieser Parameter NULL empfängt, wenn `dwReturnMask` schließt nicht den SCRIPTINFO_ITYPEINFO-Wert, oder ob Typinformationen nicht für diesen Artikel verfügbar ist. Wenn Typinformationen nicht verfügbar ist, das Objekt kann nicht Ereignissen der Datenquelle und namensbindung muss realisiert werden, mit der `IDispatch::GetIDsOfNames` Methode. Beachten Sie, dass die `ITypeInfo` Schnittstelle abgerufen wird Co-Klasse des Elements (TKIND_COCLASS) beschrieben, da das Objekt mehrere Schnittstellen und Ereignisschnittstellen unterstützen kann. Wenn das Element unterstützt die `IProvideMultipleTypeInfo` -Schnittstelle, die `ITypeInfo` Schnittstelle abgerufen ist identisch mit dem Index 0 (null) `ITypeInfo` , würden mit abgerufen werden die `IProvideMultipleTypeInfo::GetInfoOfIndex` Methode.  
  
## <a name="return-value"></a>Rückgabewert  
 Gibt einen der folgenden Werte zurück:  
  
|Rückgabewert|Bedeutung|  
|------------------|-------------|  
|`S_OK`|Erfolgreich.|  
|`E_INVALIDARG`|Ein Argument war ungültig.|  
|`E_POINTER`|Es wurde ein ungültiger Zeiger angegeben.|  
|`TYPE_E_ELEMENTNOTFOUND`|Ein Element mit dem angegebenen Namen wurde nicht gefunden.|  
  
## <a name="remarks"></a>Hinweise  
 Diese Methode ruft nur die Informationen, die vom angegebenen ab der `dwReturnMask` -Parameter ist; dies verbessert die Leistung. Z. B. wenn ein `ITypeInfo` Schnittstelle ist nicht erforderlich, für ein Element, einfach nicht angegeben ist `dwReturnMask`.  
  
## <a name="see-also"></a>Siehe auch  
 [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md)