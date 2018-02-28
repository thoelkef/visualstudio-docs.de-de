---
title: IActiveScript::AddNamedItem | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- IActiveScript.AddNamedItem
apilocation:
- scrobj.dll
helpviewer_keywords:
- AddNamedItem method, IActiveScript interface
ms.assetid: a7c6317d-948f-4bb3-b169-1bbe5b7c7cc5
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: db65361e4bde14e803d9085a4530a505ccaf9fcb
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptaddnameditem"></a>IActiveScript::AddNamedItem
Das Skriptmodul Namespace hinzugefügt der Name eines Elements auf der Stammebene. Ein Element auf der Stammebene ist ein Objekt mit Eigenschaften und Methoden, die eine Ereignisquelle oder alle drei.  
  
## <a name="syntax"></a>Syntax  
  
```  
HRESULT AddNamedItem(  
    LPCOLESTR pstrName,  // address of item name  
    DWORD dwFlags          // item flags  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pstrName`  
 [in] Die Adresse eines Puffers, der den Namen des Elements enthält, wie aus dem Skript angezeigt. Der Name muss eindeutig und dauerhaft sein.  
  
 `dwFlags`  
 [in] Flags, die einem Element zugeordnet werden. Es kann eine Kombination dieser Werte sein:  
  
|Wert|Bedeutung|  
|-----------|-------------|  
|SCRIPTITEM_CODEONLY|Gibt an, dass das benannte Element einer reinen Objekt darstellt und der Host enthält keine `IUnknown` dieses reinen-Objekt zugeordnet werden soll. Der Host hat nur einen Namen für dieses Objekt. In objektorientierten Sprachen wie C++ würde dieses Flag eine Klasse erstellen. Nicht alle Sprachen unterstützen dieses Flag.|  
|SCRIPTITEM_GLOBALMEMBERS|Gibt an, dass das Element eine Auflistung von globalen Eigenschaften und Methoden, die dem Skript zugeordnet ist. Normalerweise würde ein Skriptmodul ignorieren den Objektnamen (außer für die Verwendung als Cookie für die [IActiveScriptSite::GetItemInfo](../../winscript/reference/iactivescriptsite-getiteminfo.md) -Methode, oder zum Auflösen von expliziten Bereichsdefinition) und dessen Member als global verfügbar machen Variablen und Methoden. Dadurch wird den Host in der Bibliothek (Laufzeitfunktionen usw.) für das Skript verfügbar zu erweitern. Es obliegt dem Skriptmodul für den Umgang mit Namen in Konflikt stehen (z. B. wenn zwei SCRIPTITEM_GLOBALMEMBERS-Elemente Methoden mit demselben Namen vorhanden sind), obwohl ein Fehler aufgrund dieser Situation nicht zurückgegeben werden sollen.|  
|SCRIPTITEM_ISPERSISTENT|Gibt an, dass das Element gespeichert werden soll, wenn das Skriptmodul gespeichert wird. Auf ähnliche Weise gibt dieses Flag an, dass das Element Name und Typ-Informationen (das Skriptmodul muss alle Verweise auf Schnittstellen auf das eigentliche Objekt jedoch Version) ein Übergang zurück zum initialisierten Zustand beibehalten werden sollen.|  
|SCRIPTITEM_ISSOURCE|Gibt an, dass das Element Ereignisquelle, die das Skript empfangen können. Untergeordnete Objekte (Eigenschaften des Objekts in sich selbst Objekte sind) können Ereignisse an das Skript auch Datenquellen. Dies ist nicht rekursiv, aber es bietet eine bequeme den meisten Fällen, z. B. zum Erstellen eines Containers und alle seine Member Steuerelemente.|  
|SCRIPTITEM_ISVISIBLE|Gibt an, dass der Name des Elements im Namespace des Skripts, den Zugriff auf die Eigenschaften, Methoden und Ereignisse des Elements verfügbar ist. Gemäß der Konvention sind die Eigenschaften des Elements das Element untergeordnete Elemente: aus diesem Grund alle untergeordneten Objekteigenschaften und Methoden (und ihre untergeordneten rekursiv) zugegriffen werden.|  
|SCRIPTITEM_NOCODE|Gibt an, dass das Element ist einfach ein Name, den Skriptnamensbereich hinzugefügt wird, und nicht als ein Element, das für den Code zugeordnet sein sollte behandelt werden soll. Z. B. Wenn dieses Kennzeichen nicht festgelegt wird, VBScript wird kein separates Modul für den Namen des Elements erstellt, und C++ kann eine separate Wrapperklasse für den Namen des Elements erstellen.|  
  
## <a name="return-value"></a>Rückgabewert  
 Gibt einen der folgenden Werte zurück:  
  
|Rückgabewert|Bedeutung|  
|------------------|-------------|  
|`S_OK`|Erfolgreich.|  
|`E_INVALIDARG`|Ein Argument war ungültig.|  
|`E_POINTER`|Es wurde ein ungültiger Zeiger angegeben.|  
|`E_UNEXPECTED`|Der Aufruf wurde nicht erwartet (z. B. das Skriptmodul wurde noch kein geladen oder initialisiert).|  
  
## <a name="see-also"></a>Siehe auch  
 [IActiveScript](../../winscript/reference/iactivescript.md)