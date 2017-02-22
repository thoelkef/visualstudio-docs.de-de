---
title: "IDiaReadExeAtOffsetCallback | Microsoft Docs"
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
  - "IDiaReadExeAtOffsetCallback-Schnittstelle"
ms.assetid: 3c961641-3ce3-4bc3-bd6e-a802fa3bec49
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaReadExeAtOffsetCallback
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Aktiviert eine Clientanwendung Bytes einer ausführbaren Datei angeben, wie von Dateiposition angegeben.  
  
## Syntax  
  
```  
IDiaReadExeAtOffsetCallback : IUnknown  
```  
  
## Methoden in die Vtable\-Reihenfolge  
 In der folgenden Tabelle werden die Methoden von `IDiaReadExeAtOffsetCallback`an.  
  
|Methode|Beschreibung|  
|-------------|------------------|  
|[IDiaReadExeAtOffsetCallback::ReadExecutableAt](../../debugger/debug-interface-access/idiareadexeatoffsetcallback-readexecutableat.md)|Liest die angegebene Anzahl von Bytes, die am angegebenen Offset aus einer ausführbaren Datei starten.|  
  
## Hinweise  
 Die Clientanwendung implementiert diese Schnittstelle, um die Bytes der ausführbaren Datei mit einem absoluten Offsets in die Datei der ausführbaren Datei bereitzustellen.  Um eine relative virtuelle Adresse zu verwenden, implementieren Sie die [IDiaReadExeAtRVACallback](../../debugger/debug-interface-access/idiareadexeatrvacallback.md)\-Schnittstelle.  
  
## Hinweise für Aufrufer  
 Diese Methode wird von der Clientanwendung implementiert und [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md) die Methode als alternative Methode zum Lesen der Datei übergeben.  
  
## Anforderungen  
 Header: Dia2.h  
  
 Bibliothek: diaguids.lib  
  
 DLLs: msdia80.dll  
  
## Siehe auch  
 [Schnittstellen \(Debug Interface Access SDK\)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)   
 [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)   
 [IDiaReadExeAtRVACallback](../../debugger/debug-interface-access/idiareadexeatrvacallback.md)