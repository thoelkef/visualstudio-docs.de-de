---
title: "IDiaSession::findFile | Microsoft Docs"
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
  - "IDiaSession::findFile-Methode"
ms.assetid: a215dc21-b316-40d7-9923-55bfa014976b
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaSession::findFile
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Ruft Quelldateien nach Kompiliereinheit und Namen ab.  
  
## Syntax  
  
```cpp#  
HRESULT findFile (   
   IDiaSymbol*           pCompiland,  
   LPCOLESTR             name,  
   DWORD                 option,  
   IDiaEnumSourceFiles** ppResult  
);  
```  
  
#### Parameter  
 `pCompiland`  
 \[in\] Ein [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)\-Objekt, das die als Kontext für die Suche zu verwendende Kompiliereinheit darstellt.  Legen Sie diesen Parameter auf `NULL` fest, um Quelldateien in allen Kompiliereinheiten zu suchen.  
  
 `name`  
 \[in\] Gibt die Namen der Quelldateien an, die abgerufen werden sollen.  Legen Sie diesen Parameter auf `NULL` fest, damit alle Quelldateien abgerufen werden können.  
  
 `option`  
 \[in\] Gibt die Vergleichsoptionen an, die auf Namenssuchen angewendet werden sollen.  Werte aus der [NameSearchOptions Enumeration](../../debugger/debug-interface-access/namesearchoptions.md)\-Enumeration können einzeln oder in Kombination verwendet werden.  
  
 `ppResult`  
 \[out\] Gibt ein [IDiaEnumSourceFiles](../../debugger/debug-interface-access/idiaenumsourcefiles.md)\-Objekt zurück, das eine Liste der abgerufenen Quelldateien enthält.  
  
## Rückgabewert  
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.  
  
## Beispiel  
  
```cpp#  
IDiaEnumSourceFiles* pEnum;  
pSession->findFile( NULL, L"sourcefile.cpp", nsFNameExt, &pEnum );  
```  
  
## Siehe auch  
 [IDiaEnumSourceFiles](../../debugger/debug-interface-access/idiaenumsourcefiles.md)   
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [NameSearchOptions Enumeration](../../debugger/debug-interface-access/namesearchoptions.md)