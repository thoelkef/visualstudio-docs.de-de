---
title: "IDiaDataSource::openSession | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "IDiaDataSource::openSession-Methode"
ms.assetid: a3319ed0-3979-483b-9852-c0af96852c48
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# IDiaDataSource::openSession
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Öffnet eine Sitzung zum Abfragen von Symbolen.  
  
## Syntax  
  
```cpp#  
HRESULT openSession (   
   IDiaSession** ppSession  
);  
```  
  
#### Parameter  
 ppSession  
 \[out\]  Gibt ein [IDiaSession](../../debugger/debug-interface-access/idiasession.md)\-Objekt zurück, das den öffentlichen Sitzung darstellt.  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück. andernfalls gibt einen Fehlercode zurück.  In der folgenden Tabelle werden die möglichen Rückgabewerte für diese Methode auf.  
  
|Wert|Beschreibung|  
|----------|------------------|  
|E\_UNEXPECTED|Das Objekt ist nicht [IDiaDataSource](../../debugger/debug-interface-access/idiadatasource.md) bereits mit einer Quelle mit Symbolen initialisiert.|  
|E\_INVALIDARG|Ungültiger `ppSession`\-Parameter.|  
|E\_OUTOFMEMORY|Unzulänglicher Speicher, in den der Sitzung zu öffnen.|  
  
## Hinweise  
 Diese Methode öffnet ein [IDiaSession](../../debugger/debug-interface-access/idiasession.md)\-Objekt für eine Datenquelle.  
  
 `IDiaSession`\-Objekte implementieren Abfragen in der Datenquelle.  Eine Sitzung verwaltet einen Adressraum für jeden Satz Debugsymbole.  Wenn die EXE\-Datei oder DLL\-Datei, die durch die Symbole Datenquellen beschrieben wird, Mehradressen in den Bereichen aktiv ist \(z. B. weil mehrere Prozesse sie geladen wurden\), sollte eine Sitzung für jeden Adressbereich verwendet werden.  
  
## Beispiel  
  
```cpp#  
IDiaSession* pSession;  
HRESULT hr = pSource->openSession( &pSession );  
if (FAILED(hr))  
{  
   // report error  
}  
```  
  
## Siehe auch  
 [IDiaDataSource](../../debugger/debug-interface-access/idiadatasource.md)   
 [Übersicht](../../debugger/debug-interface-access/overview-debug-interface-access-sdk.md)   
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)   
 [Abfragen der PDB\-Datei](../../debugger/debug-interface-access/querying-the-dot-pdb-file.md)