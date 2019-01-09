---
title: IActiveScriptAuthor::AddNamedItem | Microsoft-Dokumentation
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
ms.openlocfilehash: 85c434ea17d41fb98300289c3161349f9d9f5a2f
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/08/2019
ms.locfileid: "54094860"
---
# <a name="iactivescriptauthoraddnameditem"></a>IActiveScriptAuthor::AddNamedItem
Fügt den Namen eines Elements auf der Stammebene an das Skript-Engine-Namespace erstellen. Ein *auf Stammebene Element* ist ein Objekt, das Eigenschaften und Methoden enthalten kann, und eine Ereignisquelle enthalten können.  
  
## <a name="syntax"></a>Syntax  
  
```cpp
HRESULT AddNamedItem(  
   LPCOLESTR          pszName,  
   DWORD              dwFlags,  
   IDispatch          *pdisp  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pszName`  
 [in] Der Name des Elements, wie aus dem Skript angezeigt werden soll. Der Name muss eindeutig und dauerhaft sein.  
  
 `dwFlags`  
 [in] Die Flags, die den Namen des Elements zugeordnet sind. Eine Kombination der folgenden Werte sind möglich:  
  
|Konstante|Wert|Beschreibung|  
|--------------|-----------|-----------------|  
|SCRIPTITEM_ISVISIBLE|0x00000002|Gibt an, dass der Name des Elements im Namespace des Skripts verfügbar ist. Dies ermöglicht den Zugriff auf Eigenschaften, Methoden und Ereignisse des Elements.<br /><br /> Standardmäßig enthalten die Eigenschaften des Elements, die untergeordneten Elemente des Elements. Aus diesem Grund alle untergeordneten Objekt – Eigenschaften und Methoden (und ihre untergeordneten Elemente rekursiv) zugegriffen werden.|  
|SCRIPTITEM_ISSOURCE|0x00000004|Gibt an, die Quelle der Ereignisse, dass das Skript Skript-Ereignishandler verwenden kann.|  
|SCRIPTITEM_GLOBALMEMBERS|0x00000008|Gibt an, dass das Element ist eine Auflistung von globalen Eigenschaften und Methoden, die mit dem Skript zugeordnet sind. Member werden als globale Variablen und Methoden erstellt.|  
|SCRIPTITEM_ISPERSISTENT|0x00000040|Gibt an, dass das Element gespeichert werden soll, wenn das Skript-Engine-Erstellung gespeichert wird.|  
|SCRIPTITEM_CODEONLY|0x00000200|Gibt an, dass der Namen des Elements, ein Objekt nur mit Code darstellt, und er verfügt nicht über ein Element zu erstellen.|  
|SCRIPTITEM_NOCODE|0x00000400|Gibt an, dass das benannte Element ist nur ein Name, die hinzugefügt wird, und dies hat nichts zu erstellen.|  
  
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