---
title: IActiveScriptAuthor::AddNamedItem | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptAuthor.AddNamedItem
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptAuthor::AddNamedItem
ms.assetid: 951003b6-1c4a-4086-b7ce-2f128e007280
caps.latest.revision: 19
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 83d2597f8468bb97d20da655a56a751191ec4b55
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
ms.locfileid: "24645610"
---
# <a name="iactivescriptauthoraddnameditem"></a>IActiveScriptAuthor::AddNamedItem
Fügt den Namen eines Elements auf der Stammebene an das Skript des Moduls Namespace erstellen. Ein *Element auf der Stammebene* ist ein Objekt, das Eigenschaften und Methoden enthalten kann, und eine Ereignisquelle enthalten können.  
  
## <a name="syntax"></a>Syntax  
  
```  
HRESULT AddNamedItem(  
   LPCOLESTR          pszName,  
   DWORD              dwFlags,  
   IDispatch          *pdisp  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pszName`  
 [in] Der Name des Elements aus dem Skript angezeigt. Der Name muss eindeutig und dauerhaft sein.  
  
 `dwFlags`  
 [in] Die Flags, die den Namen des Elements zugeordnet sind. Eine Kombination der folgenden Werte ist möglich:  
  
|Konstante|Wert|Beschreibung|  
|--------------|-----------|-----------------|  
|SCRIPTITEM_ISVISIBLE|0x00000002|Gibt an, dass der Name des Elements im Namespace des Skripts verfügbar ist. Dies ermöglicht den Zugriff auf des Elements-Eigenschaften, Methoden und Ereignisse.<br /><br /> Gemäß der Konvention enthält die Eigenschaften des Elements das Element untergeordnete Elemente. Aus diesem Grund alle untergeordneten Objekteigenschaften und Methoden (und ihre untergeordneten Elemente rekursiv) zugegriffen werden.|  
|SCRIPTITEM_ISSOURCE|0x00000004|Gibt an, die Elementquelle-Ereignisse, das Skript Skriptereignisse erzielt werden kann.|  
|SCRIPTITEM_GLOBALMEMBERS|0x00000008|Gibt an, dass das Element ist eine Auflistung von globalen Eigenschaften und Methoden, die dem Skript zugeordnet sind. Die Elemente werden als globale Variablen und Methoden erstellt.|  
|SCRIPTITEM_ISPERSISTENT|0x00000040|Gibt an, dass das Element gespeichert werden soll, wenn das Modul authoring Skript gespeichert ist.|  
|SCRIPTITEM_CODEONLY|0x00000200|Gibt an, dass der Namen des Elements, ein Objekt nur Code darstellt, und es muss kein Mitglied zu erstellen.|  
|SCRIPTITEM_NOCODE|0x00000400|Gibt an, dass das benannte Element ist nur ein hinzuzufügende Name, und er hat keinerlei erstellen.|  
  
 `pdisp`  
 [in] Die `IDispatch` von der `NamedItem` -Objekt, das Sammeln von Methoden, Eigenschaften oder die Ereignisquelle verwendet wird.  
  
## <a name="return-value"></a>Rückgabewert  
 Eine `HRESULT`. Mögliches Werte (aber nicht die Einzigen) sind die in der folgenden Tabelle.  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
  
## <a name="remarks"></a>Hinweise  
  
## <a name="see-also"></a>Siehe auch  
 [IActiveScriptAuthor-Schnittstelle](../../winscript/reference/iactivescriptauthor-interface.md)   
 [IActiveScriptAuthor::RemoveNamedItem](../../winscript/reference/iactivescriptauthor-removenameditem.md)