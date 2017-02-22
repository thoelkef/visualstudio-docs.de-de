---
title: "IDiaReadExeAtRVACallback | Microsoft Docs"
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
  - "IDiaReadExeAtRVACallback-Schnittstelle"
ms.assetid: b2892513-3952-4f99-9b98-60cb9b1fdc91
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaReadExeAtRVACallback
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Aktiviert eine Clientanwendung Bytes einer ausführbaren Datei angeben, die durch eine relative virtuelle Adresse angegeben.  
  
## Syntax  
  
```  
IDiaReadExeAtRVACallback : IUnknown  
```  
  
## Methoden in die Vtable\-Reihenfolge  
 In der folgenden Tabelle werden die Methoden von `IDiaReadExeAtRVACallback`an.  
  
|Methode|Beschreibung|  
|-------------|------------------|  
|[IDiaReadExeAtRVACallback::ReadExecutableAtRVA](../../debugger/debug-interface-access/idiareadexeatrvacallback-readexecutableatrva.md)|Liest die angegebene Anzahl von Bytes, die an der angegebenen relativen virtuellen Adresse \(RVA\) beginnen mit der ausführbaren Datei.|  
  
## Hinweise  
 Die Clientanwendung implementiert diese Schnittstelle, um die Bytes der ausführbaren Datei mit einer relativen virtuellen Adresse in die Datei der ausführbaren Datei bereitzustellen.  Um einen Offset der absoluten Datei zu verwenden, implementieren Sie die [IDiaReadExeAtOffsetCallback](../../debugger/debug-interface-access/idiareadexeatoffsetcallback.md)\-Schnittstelle.  
  
## Hinweise für Aufrufer  
 Diese Methode wird von der Clientanwendung implementiert und [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md) die Methode als alternative Methode zum Lesen der Datei übergeben.  
  
## Anforderungen  
 Header: Dia2.h  
  
 Bibliothek: diaguids.lib  
  
 DLLs: msdia80.dll  
  
## Siehe auch  
 [Schnittstellen \(Debug Interface Access SDK\)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)   
 [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)   
 [IDiaReadExeAtOffsetCallback](../../debugger/debug-interface-access/idiareadexeatoffsetcallback.md)