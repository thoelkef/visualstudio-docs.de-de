---
title: "IDiaSession::findChildren | Microsoft Docs"
ms.custom: ""
ms.date: "12/02/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "IDiaSession::findChildren-Methode"
ms.assetid: 5d19046f-f668-4aa9-8788-95cda9a98997
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaSession::findChildren
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Ruft alle untergeordneten Elemente eines angegebenen Elementen Bezeichners ab, die den Namen und den Typ des Symbols übereinstimmen.  
  
## Syntax  
  
```cpp#  
HRESULT findChildren (   
   IDiaSymbol*       parent,  
   SymTagEnum        symtag,  
   LPCOLESTR         name,  
   DWORD             compareFlags,  
   IDiaEnumSymbols** ppResult  
);  
```  
  
#### Parameter  
 `parent`  
 \[in\]  Ein [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)\-Objekt, das das übergeordnete Element darstellt.  Wenn dieses Symbol Elemente eine Funktion, Modul\- oder Block befindet, werden die lexikalischen untergeordneten Elemente in `ppResult`zurückgegeben.  Wenn das übergeordnete Symbol ein Typ ist, werden die zugehörigen Klassen untergeordneten Elemente zurückgegeben.  Wenn dieser Parameter `NULL`ist, muss `symtag` zu `SymTagExe` oder `SymTagNull`festgelegt werden, der den globalen Bereich \(EXE\-Datei\) zurückgibt.  
  
 `symtag`  
 \[in\]  Gibt das Symbol tag der untergeordneten Elemente an, die abgerufen werden sollen.  Werte werden von der [SymTagEnum\-Enumeration](../../debugger/debug-interface-access/symtagenum.md)\-Enumeration bestimmt.  Auf `SymTagNull` , um alle untergeordneten Elemente abzurufen.  
  
 `name`  
 \[in\]  Gibt den Namen der untergeordneten Elemente an, die abgerufen werden sollen.  Auf `NULL` , sodass alle untergeordneten Elemente abgerufen werden können.  
  
 `compareFlags`  
 \[in\]  Gibt die Vergleichsoptionen, die angewendet werden, um Übereinstimmungen zu benennen.  Werte aus der [NameSearchOptions Enumeration](../../debugger/debug-interface-access/namesearchoptions.md)\-Enumeration können allein oder in Kombination verwendet werden.  
  
 `ppResult`  
 \[out\]  Gibt ein [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)\-Objekt zurück, das die Liste der untergeordneten abgerufenen Symbole enthält.  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück. andernfalls gibt einen Fehlercode zurück.  
  
## Beispiel  
 Im folgenden Beispiel wird gezeigt, wie lokale Variablen der Funktion `pFunc` Übereinstimmungen sucht die Namen `szVarName`.  
  
```cpp#  
IDiaEnumSymbols* pEnum;  
pSession->findChildren( pFunc, SymTagData, szVarName, nsCaseSensitive, &pEnum );  
```  
  
## Siehe auch  
 [Übersicht](../../debugger/debug-interface-access/overview-debug-interface-access-sdk.md)   
 [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)   
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [NameSearchOptions Enumeration](../../debugger/debug-interface-access/namesearchoptions.md)   
 [SymTagEnum\-Enumeration](../../debugger/debug-interface-access/symtagenum.md)