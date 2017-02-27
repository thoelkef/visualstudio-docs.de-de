---
title: "IDiaSession::findInjectedSource | Microsoft Docs"
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
  - "IDiaSession::findInjectedSource-Methode"
ms.assetid: 907531b6-1ef8-4153-986d-b72611a1632d
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# IDiaSession::findInjectedSource
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Ruft eine Liste von Quellen ab, die in den Symbolspeicher durch Anbieter Attribut oder anderen Komponenten des Prozesses Kompilierung platziert wurde.  
  
## Syntax  
  
```cpp#  
HRESULT findInjectedSource (   
   LPCOLESTR                 srcFile,  
   IDiaEnumInjectedSources** ppResult  
);  
```  
  
#### Parameter  
 srcFile  
 \[in\]  Name der Quelldatei, sodass die gesucht werden soll.  
  
 ppResult  
 \[out\]  Gibt ein [IDiaEnumInjectedSources](../../debugger/debug-interface-access/idiaenuminjectedsources.md)\-Objekt zurück, das eine Liste aller eingefügten Quellen enthält.  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück. andernfalls gibt einen Fehlercode zurück.  
  
## Siehe auch  
 [IDiaEnumInjectedSources](../../debugger/debug-interface-access/idiaenuminjectedsources.md)   
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)