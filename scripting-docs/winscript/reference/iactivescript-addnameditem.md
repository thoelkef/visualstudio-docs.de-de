---
title: "IActiveScript::AddNamedItem | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScript.AddNamedItem
apilocation: scrobj.dll
helpviewer_keywords: 
  - "AddNamedItem-Methode, IActiveScript-Schnittstelle"
ms.assetid: a7c6317d-948f-4bb3-b169-1bbe5b7c7cc5
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IActiveScript::AddNamedItem
Fügt den Namen eines Elements auf Stammebene den Namespace des Skriptmoduls hinzu.  Ein Element auf der Stammebene ist ein Objekt mit Eigenschaften und Methoden, eine Ereignisquelle oder alle drei.  
  
## Syntax  
  
```  
HRESULT AddNamedItem(  
    LPCOLESTR pstrName,  // address of item name  
    DWORD dwFlags          // item flags  
);  
```  
  
#### Parameter  
 `pstrName`  
 \[in\] Adresse eines Puffers, der den Namen des Elements enthält, wie im Skript angezeigt.  Der Name muss eindeutig sein und bleiben.  
  
 `dwFlags`  
 \[in\] Flags mit einem Element zugeordnet.  Kann eine Kombination dieser Werte:  
  
|Wert|Bedeutung|  
|----------|---------------|  
|SCRIPTITEM\_CODEONLY|Gibt an, dass das genannte Element ein nur für Code Objekt darstellt und dass der Host kein mit diesem hat nur für Code Objekt zugeordnet werden `IUnknown`.  Der Host verfügt über einen Namen für dieses Objekt.  In objektorientierten Sprachen wie C\+\+, würde dieses Flag eine Klasse erstellen.  Nicht alle Sprachen unterstützen dieses Flag.|  
|SCRIPTITEM\_GLOBALMEMBERS|Gibt an, dass das Element eine Auflistung globale Eigenschaften und Methoden ist, die dem Skript zugeordnet sind.  Normalerweise würde ein Skriptmodul den Objektnamen \(außer, mit dem Ziel die Anwendung er als Cookie für die [IActiveScriptSite::GetItemInfo](../../winscript/reference/iactivescriptsite-getiteminfo.md)\-Methode oder zum Auflösen des expliziten Bewertens\) ignorieren und seine Member als globale Variablen und Methoden verfügbar machen.  Dies ermöglicht es dem Host, die Bibliothek \(Laufzeitfunktionen. usw.\) zu erweitern für das Skript.  Es wird dem Skriptmodul überlassen, um Namenskonflikte zu verarbeiten \(beispielsweise, wenn zwei SCRIPTITEM\_GLOBALMEMBERS\-Elemente Methoden des gleichen Namens haben\), wobei ein Fehler nicht zurückgegebene Situation deswegen sein sollte.|  
|SCRIPTITEM\_ISPERSISTENT|Gibt an, dass das Element gespeichert werden soll, wenn das Skriptmodul gespeichert wird.  Entsprechend Festlegen dieses Flag gibt an, dass ein Übergang zurück zum initialisierten Zustand den Namen des Elements und die Typinformationen \(das Skriptmodul muss alle Zeiger Schnittstellen auf den tatsächlichen Objekt jedoch freigeben\) beibehalten soll.|  
|SCRIPTITEM\_ISSOURCE|Gibt an, dass die Elementquellereignisse die das Skript empfangen kann.  Untergeordnete Objekte \(Eigenschaften des Objekts, die in selbst Objekte sind\), können auch Ereignisse hervorruft dem Skript.  Dies ist nicht rekursiv, jedoch stellt einen geeigneten Mechanismus für den allgemeinen Fall zum Beispiel für das Erstellen eines Containers und der aller seine Membersteuerelementen bereit.|  
|SCRIPTITEM\_ISVISIBLE|Gibt an, dass der Name des Elements im Namespace des Skripts verfügbar ist und Zugriff auf Eigenschaften, Methoden und Ereignisse des Elements festlegen.  Standardmäßig enthalten die Eigenschaften des Elements die untergeordneten Elemente des Elements; Daher sind alle untergeordneten Objekteigenschaften und \-methoden \(und ihre untergeordneten Elemente, rekursiv\) zugänglich.|  
|SCRIPTITEM\_NOCODE|Gibt, an, dass das Element einfach ein Name, der dem Namespace des Skripts hinzugefügt wird, und sollte nicht behandelt werden als Element, für das Code zugeordnet werden soll.  Beispielsweise ohne dieses Flag, das festgelegt wird, erstellt VBScript ein separates Modul für das genannte Element, C\+\+ und erstellt möglicherweise eine eigene Wrapperklasse für das genannte Element.|  
  
## Rückgabewert  
 Gibt eine der folgenden Werte:  
  
|Rückgabewert|Bedeutung|  
|------------------|---------------|  
|`S_OK`|Erfolgreich.|  
|`E_INVALIDARG`|Ein Argument war ungültig.|  
|`E_POINTER`|Ein ungültiger Zeiger wurde angegeben.|  
|`E_UNEXPECTED`|Der Aufruf wurde nicht erwartet \(beispielsweise, ist das Skriptmodul noch nicht geladen wurde oder initialisiert wurden\).|  
  
## Siehe auch  
 [IActiveScript](../../winscript/reference/iactivescript.md)