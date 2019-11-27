---
title: 'Iactivescriptauthor:: addnameditem | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 01/18/2017
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
ms.openlocfilehash: f0d2f08a49fdc768e87152bf486ce48687c79e68
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/18/2019
ms.locfileid: "72577255"
---
# <a name="iactivescriptauthoraddnameditem"></a>IActiveScriptAuthor::AddNamedItem
Fügt dem Namespace der Skript Erstellungs-Engine den Namen eines Elements auf Stamm Ebene hinzu. Ein *Element* auf Stamm Ebene ist ein Objekt, das Eigenschaften und Methoden enthalten kann und auch eine Ereignis Quelle enthalten kann.  
  
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
 in Der Name des Elements, das im Skript angezeigt wird. Der Name muss eindeutig und dauerhaft sein.  
  
 `dwFlags`  
 in Die Flags, die dem benannten Element zugeordnet sind. Kann eine Kombination der folgenden Werte sein:  
  
|Konstante|Wert|Beschreibung|  
|--------------|-----------|-----------------|  
|SCRIPTITEM_ISVISIBLE|0x00000002|Gibt an, dass der Name des Elements im Namespace des Skripts verfügbar ist. Dadurch wird der Zugriff auf die Eigenschaften, Methoden und Ereignisse des Elements ermöglicht.<br /><br /> Gemäß der Konvention enthalten die Eigenschaften des Elements die untergeordneten Elemente des Elements. Daher können Sie auf alle untergeordneten Objekteigenschaften und-Methoden (und deren untergeordnete Elemente rekursiv) zugreifen.|  
|SCRIPTITEM_ISSOURCE|0x00000004|Gibt die Ereignisse der Element Quelle an, die das Skript Skript Ereignishandler aufweisen kann.|  
|SCRIPTITEM_GLOBALMEMBERS|0x00000008|Gibt an, dass das Element eine Auflistung globaler Eigenschaften und Methoden ist, die dem Skript zugeordnet sind. Seine Member werden als globale Variablen und Methoden erstellt.|  
|SCRIPTITEM_ISPERSISTENT|0x00000040|Gibt an, dass das Element gespeichert werden soll, wenn die Skript Erstellungs-Engine gespeichert wird.|  
|SCRIPTITEM_CODEONLY|0x00000200|Gibt an, dass das benannte Element ein nur-Code-Objekt darstellt und keinen Member für die Erstellung hat.|  
|SCRIPTITEM_NOCODE|0x00000400|Gibt an, dass das benannte Element nur ein Name ist, der hinzugefügt wird, und hat nichts zu erstellen.|  
  
 `pdisp`  
 in Die `IDispatch` des `NamedItem` Objekts, das zum Erfassen von Methoden, Eigenschaften oder der Ereignis Quelle verwendet wird.  
  
## <a name="return-value"></a>Rückgabewert  
 Ein `HRESULT`. Mögliches Werte (aber nicht die Einzigen) sind die in der folgenden Tabelle.  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
  
## <a name="remarks"></a>Hinweise  
  
## <a name="see-also"></a>Siehe auch  
 [Iactivescriptauthor-Schnittstelle](../../winscript/reference/iactivescriptauthor-interface.md)   
 [IActiveScriptAuthor::RemoveNamedItem](../../winscript/reference/iactivescriptauthor-removenameditem.md)