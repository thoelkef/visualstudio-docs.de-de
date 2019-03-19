---
title: Addnameditem | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScript.AddNamedItem
apilocation:
- scrobj.dll
helpviewer_keywords:
- AddNamedItem method, IActiveScript interface
ms.assetid: a7c6317d-948f-4bb3-b169-1bbe5b7c7cc5
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: db0a97c01d948a0c26850ebd1c3f47c6e3900614
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/19/2019
ms.locfileid: "58151855"
---
# <a name="iactivescriptaddnameditem"></a>IActiveScript::AddNamedItem
Der Name eines Elements auf der Stammebene und die Skript-Engine-Namespace hinzugefügt. Ein Element auf Stammebene ist ein Objekt mit Eigenschaften und Methoden, eine Ereignisquelle oder alle drei.  
  
## <a name="syntax"></a>Syntax  
  
```cpp
HRESULT AddNamedItem(  
    LPCOLESTR pstrName,  // address of item name  
    DWORD dwFlags          // item flags  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pstrName`  
 [in] Die Adresse eines Puffers, die den Namen des Elements enthält, wie Sie aus dem Skript angezeigt. Der Name muss eindeutig und dauerhaft sein.  
  
 `dwFlags`  
 [in] Flags, die einem Element zugeordnet werden. Es kann eine Kombination dieser Werte sein:  
  
|Wert|Bedeutung|  
|-----------|-------------|  
|SCRIPTITEM_CODEONLY|Gibt an, dass es sich bei der Namen des Elements ein Objekt nur mit Code darstellt und der Host enthält keine `IUnknown` dieses Objekt nur mit Code zugeordnet werden soll. Der Host kann nur einen Namen für dieses Objekt. In objektorientierten Sprachen wie C++ würde dieses Flag auf eine Klasse erstellen. Nicht alle Sprachen unterstützen dieses Flag.|  
|SCRIPTITEM_GLOBALMEMBERS|Gibt an, dass das Element eine Auflistung von globalen Eigenschaften und Methoden, die dem Skript zugeordnet ist. Normalerweise würde eine Skript-Engine den Objektnamen ignorieren (außer für die Verwendung als ein Cookie für die [iactivescriptsite:: GetItemInfo](../../winscript/reference/iactivescriptsite-getiteminfo.md) -Methode, oder für das Auflösen von expliziten Festlegen des Gültigkeitsbereichs) und dessen Member als global verfügbar machen Variablen und Methoden. Dadurch wird den Host in der Bibliothek (Laufzeitfunktionen und So weiter) für das Skript verfügbar zu erweitern. Es obliegt der Skript-Engine für den Umgang mit Namen in Konflikt steht (z. B., wenn die beiden SCRIPTITEM_GLOBALMEMBERS Elemente Methoden mit dem gleichen Namen haben), auch wenn ein Fehler aufgrund dieser Situation nicht zurückgegeben werden soll.|  
|SCRIPTITEM_ISPERSISTENT|Gibt an, dass das Element gespeichert werden soll, wenn die Skript-Engine gespeichert wird. Auf ähnliche Weise zeigt dieses Flag an, dass des Elements Name und Typ-Informationen (die Skript-Engine muss alle Zeiger auf die Schnittstellen das eigentliche Objekt jedoch Version) ein Übergang zurück zum initialisierten Zustand beibehalten werden sollen.|  
|SCRIPTITEM_ISSOURCE|Gibt an, dass das Element Ereignisquelle, die das Skript empfangen können. Untergeordnete Objekte (Eigenschaften des Objekts, die in sich selbst Objekte) können Ereignisse an das Skript auch Datenquellen. Dies ist nicht rekursiv, aber es bietet eine bequeme meistens z. B. einen Container und alle seine Member Steuerelemente erstellen.|  
|SCRIPTITEM_ISVISIBLE|Gibt an, dass der Name des Elements im Namespace des Skripts, den Zugriff auf die Eigenschaften, Methoden und Ereignisse des Elements verfügbar ist. Standardmäßig sind die Eigenschaften des Elements des Elements untergeordnete Elemente: aus diesem Grund alle untergeordneten Objekt – Eigenschaften und Methoden (und deren untergeordneten Elemente rekursiv) zugegriffen werden.|  
|SCRIPTITEM_NOCODE|Gibt an, dass das Element ist einfach ein Name-Namespace des Skripts hinzugefügt wird, und nicht als ein Element, das für die Code zugeordnet sein soll behandelt werden soll. Z. B. Wenn dieses Kennzeichen nicht festgelegt wird, VBScript wird kein separates Modul für den Namen des Elements erstellt, und C++ kann eine separate Wrapperklasse für den Namen des Elements erstellen.|  
  
## <a name="return-value"></a>Rückgabewert  
 Gibt einen der folgenden Werte zurück:  
  
|Rückgabewert|Bedeutung|  
|------------------|-------------|  
|`S_OK`|Erfolgreich.|  
|`E_INVALIDARG`|Ein Argument war ungültig.|  
|`E_POINTER`|Es wurde ein ungültiger Zeiger angegeben.|  
|`E_UNEXPECTED`|Der Aufruf wurde nicht erwartet (z. B. die Skript-Engine wurde noch nicht wurden geladen oder initialisiert).|  
  
## <a name="see-also"></a>Siehe auch  
 [IActiveScript](../../winscript/reference/iactivescript.md)