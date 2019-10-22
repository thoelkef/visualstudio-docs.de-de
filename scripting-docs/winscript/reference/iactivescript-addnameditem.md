---
title: 'IActiveScript:: addnameditem | Microsoft-Dokumentation'
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
ms.openlocfilehash: a343e38b944ca36da221da39832046c19b332230
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575823"
---
# <a name="iactivescriptaddnameditem"></a>IActiveScript::AddNamedItem
Fügt dem namens Bereich der Skript-Engine den Namen eines Elements auf Stamm Ebene hinzu. Ein Element auf Stamm Ebene ist ein Objekt mit Eigenschaften und Methoden, einer Ereignis Quelle oder allen drei.  
  
## <a name="syntax"></a>Syntax  
  
```cpp
HRESULT AddNamedItem(  
    LPCOLESTR pstrName,  // address of item name  
    DWORD dwFlags          // item flags  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pstrName`  
 in Adresse eines Puffers, der den Namen des Elements enthält, das im Skript angezeigt wird. Der Name muss eindeutig und dauerhaft sein.  
  
 `dwFlags`  
 in Einem Element zugeordnete Flags. Es kann eine Kombination dieser Werte sein:  
  
|Wert|Bedeutung|  
|-----------|-------------|  
|SCRIPTITEM_CODEONLY|Gibt an, dass das benannte Element ein Code geschütztes-Objekt darstellt und dass der Host über keine `IUnknown` verfügt, die diesem reinen Code Objekt zugeordnet werden können. Der Host hat nur einen Namen für dieses Objekt. In objektorientierten Sprachen wie C++würde dieses Flag eine-Klasse erstellen. Dieses Flag wird nicht von allen Sprachen unterstützt.|  
|SCRIPTITEM_GLOBALMEMBERS|Gibt an, dass das Element eine Auflistung globaler Eigenschaften und Methoden ist, die dem Skript zugeordnet sind. Normalerweise ignoriert eine Skript-Engine den Objektnamen (außer dem Zweck der Verwendung als Cookie für die [iactivescriptsite:: getiteminfo](../../winscript/reference/iactivescriptsite-getiteminfo.md) -Methode oder zum Auflösen der expliziten Bereichs Definition) und macht seine Member als globale Variablen und Methoden verfügbar. Dadurch kann der Host die Bibliothek (Lauf Zeitfunktionen usw.) erweitern, die für das Skript verfügbar ist. Es bleibt der Skript-Engine überlassen, Namenskonflikte zu behandeln (z. b. Wenn zwei SCRIPTITEM_GLOBALMEMBERS Items Methoden desselben Namens aufweisen), obwohl ein Fehler aufgrund dieser Situation nicht zurückgegeben werden sollte.|  
|SCRIPTITEM_ISPERSISTENT|Gibt an, dass das Element gespeichert werden soll, wenn die Skript-Engine gespeichert wird. Entsprechend gibt das Festlegen dieses Flags an, dass ein Übergang zurück in den initialisierten Zustand den Namen des Elements und die Typinformationen beibehalten soll (die Skript-Engine muss jedoch alle Zeiger auf Schnittstellen auf dem eigentlichen Objekt freigeben).|  
|SCRIPTITEM_ISSOURCE|Gibt an, dass das Element Ereignisse Quellen angibt, die das Skript senken kann. Untergeordnete Objekte (Eigenschaften des Objekts, die sich in sich selbst befinden) können auch Ereignisse in das Skript einfügen. Dies ist nicht rekursiv, bietet jedoch einen praktischen Mechanismus für den allgemeinen Fall, z. b. das Erstellen eines Containers und seiner Member-Steuerelemente.|  
|SCRIPTITEM_ISVISIBLE|Gibt an, dass der Name des Elements im Namespace des Skripts verfügbar ist, sodass der Zugriff auf die Eigenschaften, Methoden und Ereignisse des Elements ermöglicht wird. Gemäß der Konvention enthalten die Eigenschaften des Elements die untergeordneten Elemente des Elements. Daher kann auf alle untergeordneten Objekteigenschaften und-Methoden (und deren untergeordnete Elemente rekursiv) zugegriffen werden.|  
|SCRIPTITEM_NOCODE|Gibt an, dass das Element einfach ein Name ist, der dem Namespace des Skripts hinzugefügt wird, und sollte nicht als Element behandelt werden, dem Code zugeordnet werden soll. Wenn dieses Flag z. b. nicht festgelegt wird, erstellt VBScript ein separates Modul für das benannte Element C++ und erstellt möglicherweise eine separate Wrapper Klasse für das benannte Element.|  
  
## <a name="return-value"></a>Rückgabewert  
 Gibt einen der folgenden Werte zurück:  
  
|Rückgabewert|Bedeutung|  
|------------------|-------------|  
|`S_OK`|Erfolgreich.|  
|`E_INVALIDARG`|Ein Argument war ungültig.|  
|`E_POINTER`|Es wurde ein ungültiger Zeiger angegeben.|  
|`E_UNEXPECTED`|Der-Befehl wurde nicht erwartet (z. b. wurde die Skript-Engine noch nicht geladen oder initialisiert).|  
  
## <a name="see-also"></a>Siehe auch  
 [IActiveScript](../../winscript/reference/iactivescript.md)