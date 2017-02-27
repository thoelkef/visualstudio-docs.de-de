---
title: "&#220;bersicht (Debug Interface Access SDK) | Microsoft Docs"
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
  - "Benutzerdefinierte Typen"
  - ".dbg-Dateien"
  - "Module"
  - "Schnittstellen [DIA-SDK]"
  - "DBG-Dateien"
  - "Prozeduren [DIA-SDK]"
  - "Ausführbare Dateien"
  - "COM-Objekte,  in DIA-SDK"
  - "Compilands"
  - "Ausführbare Bilder"
ms.assetid: 720b4479-a8bc-4fec-860e-80c1a0780405
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# &#220;bersicht (Debug Interface Access SDK)
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Verwenden Sie das DIA SDK, um die Microsoft\-Debuginformationen zuzugreifen.  Das DIA SDK stellt ein basiertes COM APIs festlegen, entfällt die Notwendigkeit, das den Code umzuschreiben, sobald Microsoft das Format der Debuginformationen ändert.  Das DIA SDK können Sie auch zum Lesen aus einem ausgewählten Satz von früheren Versionen von Debuginformationen in .pdb\- und .dbg\-Dateien, die von [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)]\-Version 5.0 und höher generiert wurden.  
  
 Jede Schnittstelle im DIA SDK stellt ein anderes COM\-Objekt dar, wenn andernfalls angegeben.  Zusätzliche Schnittstellen und somit zusätzliche Objekte, werden mithilfe von expliziten Abfragen, wie [IDiaDataSource::openSession](../../debugger/debug-interface-access/idiadatasource-opensession.md) oder [IDiaSession::findChildren](../../debugger/debug-interface-access/idiasession-findchildren.md), anstatt erstellt, indem `QueryInterface` auf vorhandenen Schnittstellenzeigern aufruft.  
  
## Siehe auch  
 [IDiaDataSource::openSession](../../debugger/debug-interface-access/idiadatasource-opensession.md)   
 [IDiaSession::findChildren](../../debugger/debug-interface-access/idiasession-findchildren.md)