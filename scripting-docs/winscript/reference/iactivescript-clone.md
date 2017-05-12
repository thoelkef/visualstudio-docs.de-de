---
title: "IActiveScript::Clone | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScript.Clone
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IActiveScript_Clone"
ms.assetid: aa000b2a-7085-448d-a422-f7adac7851cb
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IActiveScript::Clone
Klont das aktuelle Skriptmodul \(abzüglich aller aktuellen Ausführungsstandes\) und gibt ein geladenes Skriptmodul zurück, das keine Website im aktuellen Thread hat.  Die Eigenschaften dieses neuen Skriptmoduls sind mit Eigenschaften identisch, die das ursprüngliche Skriptmodul in wäre, wenn es an dem initialisierten Zustand übergehen soll.  
  
## Syntax  
  
```  
HRESULT Clone(  
    IActiveScript **ppscript  // receives pointer to IActiveScript  
);  
```  
  
#### Parameter  
 `ppscript`  
 \[out\] Adresse einer Variablen, die einen Zeiger auf die [IActiveScript](../../winscript/reference/iactivescript.md)\-Schnittstelle des geklonten Skriptmoduls empfängt.  Der Host muss eine Website erstellen und die [IActiveScript::SetScriptSite](../../winscript/reference/iactivescript-setscriptsite.md)\-Methode auf dem neuen Skriptmodul aufrufen, bevor er im initialisierten Zustand und daher verwendbar.  
  
## Rückgabewert  
 Gibt eine der folgenden Werte:  
  
|Rückgabewert|Bedeutung|  
|------------------|---------------|  
|`S_OK`|Erfolgreich.|  
|`E_NOTIMPL`|Diese Methode wird nicht unterstützt.|  
|`E_POINTER`|Ein ungültiger Zeiger wurde angegeben.|  
|`E_UNEXPECTED`|Der Aufruf wurde nicht erwartet \(beispielsweise, ist das Skriptmodul noch nicht geladen wurde oder initialisiert wurden\).|  
  
## Hinweise  
 Die `IActiveScript::Clone`\-Methode ist eine Optimierung von `IPersist*::Save`, von `CoCreateInstance` und von `IPersist*::Load`, daher sollte der Zustand des neuen Skriptmoduls der identisch sein, als ob der Zustand des ursprünglichen Skriptmoduls in ein neues Skriptmodul gespeichert und geladen wurden.  Benannte Elemente werden im geklonten Skriptmodul dupliziert, aber bestimmte Objektzeiger für jedes Element vergessen werden und werden mit der [IActiveScriptSite::GetItemInfo](../../winscript/reference/iactivescriptsite-getiteminfo.md)\-Methode abgerufen.  Dadurch kann ein identisches Objektmodell mit den threadspezifischen verwendet werden Einstiegspunkten \(einem Apartmentmodell\).  
  
 Diese Methode wird für Multithread\-Datei Serverhosts verwendet, die mehrere Instanzen desselben Skripts ausführen können.  Das Skriptmodul gibt möglicherweise `E_NOTIMPL` zurück, in diesem Fall der Host das gleiche Ergebnis erreichen kann, indem er persistenten Zustand dupliziert und eine neue Instanz des Skriptmoduls mit einer `IPersist*`\-Schnittstelle erstellt.  
  
 Diese Methode kann von NichtBasis Threads mit dem Ergebnis einer NichtBasis Legende zu den Hostobjekten oder zur [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md)\-Schnittstelle ohne aufgerufen werden.  
  
## Siehe auch  
 [IActiveScript](../../winscript/reference/iactivescript.md)