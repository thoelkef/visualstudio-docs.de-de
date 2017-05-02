---
title: "IActiveScriptSite::GetItemInfo | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptSite.GetItemInfo
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IActiveScriptSite_GetItemInfo"
ms.assetid: f859ed3b-02c1-4924-99f8-5f5bf1bf8405
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# IActiveScriptSite::GetItemInfo
Ermöglicht dem Skriptmodul, erhält Informationen über ein Element, das der [IActiveScript::AddNamedItem](../../winscript/reference/iactivescript-addnameditem.md)\-Methode hinzugefügt wird.  
  
## Syntax  
  
```  
HRESULT GetItemInfo(  
    LPCOLESTR pstrName,     // address of item name  
    DWORD dwReturnMask,     // bit mask for information retrieval  
    IUnknown **ppunkItem,   // address of pointer to item's IUnknown  
    ITypeInfo **ppTypeInfo  // address of pointer to item's ITypeInfo  
);  
```  
  
#### Parameter  
 `pstrName`  
 \[in\] Der Name mit dem Element zugeordnet, wie in der [IActiveScript::AddNamedItem](../../winscript/reference/iactivescript-addnameditem.md)\-Methode angegeben.  
  
 `dwReturnMask`  
 \[in\] Ein Bitmaskenangeben, welche Informationen zum Element zurückgegeben werden sollen.  Das Skriptmodul sollte die Mindestmenge von Informationen anfordern möglich, da einige der Rückgabeparameter \(beispielsweise, `ITypeInfo`\) beträchtliche Zeit müssen können zu laden oder zu generieren.  Kann eine Kombination der folgenden Werte:  
  
|Wert|Bedeutung|  
|----------|---------------|  
|SCRIPTINFO\_IUNKNOWN|Gibt die `IUnknown`\-Schnittstelle für dieses Element zurück.|  
|SCRIPTINFO\_ITYPEINFO|Gibt die `ITypeInfo`\-Schnittstelle für dieses Element zurück.|  
  
 `ppunkItem`  
 \[out\] Zugeordnete Adresse einer Variablen, die einen Zeiger auf die `IUnknown`\-Schnittstelle empfängt, mit dem angegebenen Element zu.  Das Skriptmodul kann die `IUnknown::QueryInterface`\-Methode verwenden, erhält die `IDispatch`\-Schnittstelle für das Element.  Dieser Parameter empfängt NULL, wenn `dwReturnMask` nicht den SCRIPTINFO\_IUNKNOWN\-Wert einschließt.  Außerdem empfängt er NULL, wenn kein Objekt vorhanden ist, das mit dem Elementnamen zugeordnet wird, Dieser Mechanismus wird verwendet, um eine einfache Klasse erstellt, als das genannte Element mit dem SCRIPTITEM\_CODEONLY\-Flag hinzugefügt wurde, das in der [IActiveScript::AddNamedItem](../../winscript/reference/iactivescript-addnameditem.md)\-Methode festgelegt wurde.  
  
 `ppTypeInfo`  
 \[out\] Zugeordnete Adresse einer Variablen, die einen Zeiger auf die `ITypeInfo`\-Schnittstelle empfängt, mit dem Element zu.  Dieser Parameter empfängt NULL, wenn `dwReturnMask` nicht den SCRIPTINFO\_ITYPEINFO\-Wert enthält oder wenn Typinformationen für dieses Element nicht verfügbar sind.  Wenn Typinformationen nicht verfügbar sind, kann das Objekt keine Ereignisse generiert, und Namensbindung muss mit der `IDispatch::GetIDsOfNames`\-Methode realisiert werden.  Beachten Sie, dass die abgerufene `ITypeInfo`\-Schnittstelle die Co\-Klasse des Elements \(TKIND\_COCLASS\) beschreibt da das Objekt möglicherweise mehrere Schnittstellen und Ereignisschnittstellen unterstützt.  Wenn das Element die `IProvideMultipleTypeInfo`\-Schnittstelle unterstützt, ist die abgerufene `ITypeInfo`\-Schnittstelle genauso, die der Index null `ITypeInfo`, der mithilfe der `IProvideMultipleTypeInfo::GetInfoOfIndex`\-Methode abgerufen würde.  
  
## Rückgabewert  
 Gibt eine der folgenden Werte:  
  
|Rückgabewert|Bedeutung|  
|------------------|---------------|  
|`S_OK`|Erfolgreich.|  
|`E_INVALIDARG`|Ein Argument war ungültig.|  
|`E_POINTER`|Ein ungültiger Zeiger wurde angegeben.|  
|`TYPE_E_ELEMENTNOTFOUND`|Ein Element des angegebenen Namens wurde nicht gefunden.|  
  
## Hinweise  
 Diese Methode ruft nur die Informationen ab, die von den `dwReturnMask`\-Parameter angegeben werden; Dies verbessert die Leistung.  Wenn beispielsweise eine `ITypeInfo`\-Schnittstelle nicht für ein Element erforderlich ist, wird es nicht einfach in `dwReturnMask` angegeben.  
  
## Siehe auch  
 [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md)