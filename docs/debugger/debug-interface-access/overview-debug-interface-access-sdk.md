---
title: "Übersicht (Debug Interface Access SDK) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- user-defined types
- .dbg files
- modules
- interfaces [DIA SDK]
- DBG files
- procedures [DIA SDK]
- executable files
- COM objects, in DIA SDK
- compilands
- executable images
ms.assetid: 720b4479-a8bc-4fec-860e-80c1a0780405
caps.latest.revision: "9"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d4cd0206e402600cbe9002c931adb7ff6a2cc680
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="overview-debug-interface-access-sdk"></a>Übersicht (Debug Interface Access SDK)
Verwenden Sie das DIA SDK Zugriff auf die Microsoft-Debuginformationen. Das DIA SDK bietet eine COM-API-Satz basierte, die entfällt die Notwendigkeit, den Code umschreiben, wenn Microsoft das Format der Debuginformationen ändert. Das DIA SDK können Sie gelesen werden, einen ausgewählten Satz von früheren Versionen von Debuginformationen, befindet sich in der PDB-Datei und .dbg-Dateien generiert werden auch [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] Versionen 5.0 und höher.  
  
 Jede Schnittstelle in DIA-SDK stellt ein anderen COM-Objekt, mit Ausnahme dar, sofern nichts anderes angegeben ist. Weitere Schnittstellen und somit zusätzliche Objekte erstellt mithilfe von Abfragen im explicit, z. B. [idiadatasource:: OpenSession](../../debugger/debug-interface-access/idiadatasource-opensession.md) oder [idiasession:: Findchildren](../../debugger/debug-interface-access/idiasession-findchildren.md), statt durch Aufrufen von `QueryInterface` auf vorhandene Schnittstellenzeiger.  
  
## <a name="see-also"></a>Siehe auch  
 [Idiadatasource:: OpenSession](../../debugger/debug-interface-access/idiadatasource-opensession.md)   
 [IDiaSession::findChildren](../../debugger/debug-interface-access/idiasession-findchildren.md)