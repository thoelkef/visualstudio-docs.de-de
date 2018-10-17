---
title: Übersicht (Debug Interface Access SDK) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- C++
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
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 741e4ee8e7b05db9d8b63b296569e268d7144dc7
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2018
ms.locfileid: "49193608"
---
# <a name="overview-debug-interface-access-sdk"></a>Übersicht (Debug Interface Access SDK)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Verwenden Sie die DIA-SDK, um die Informationen zum Debuggen von Microsoft zuzugreifen. Das DIA SDK bietet eine COM-basierte API-Satz, die entfällt die Notwendigkeit, die der Code neu geschrieben, wenn sich Microsoft das Format der Debuginformationen ändert. Die DIA-SDK können Sie gelesen werden, einen ausgewählten Satz von früheren Versionen von Debuginformationen, befindet sich in der PDB-Datei und .dbg-Dateien generiert werden auch [!INCLUDE[vcprvc](../../includes/vcprvc-md.md)] Versionen 5.0 und höher.  
  
 Jede Schnittstelle in die DIA-SDK stellt ein anderes COM-Objekt, mit Ausnahme dar, falls nicht anders. Zusätzliche Schnittstellen und daher zusätzliche Objekte werden erstellt, mithilfe von Abfragen im explicit, z. B. [idiadatasource:: OpenSession](../../debugger/debug-interface-access/idiadatasource-opensession.md) oder [idiasession:: Findchildren](../../debugger/debug-interface-access/idiasession-findchildren.md), anstatt durch Aufrufen von `QueryInterface` für vorhandene Schnittstellenzeiger auf.  
  
## <a name="see-also"></a>Siehe auch  
 [Idiadatasource:: OpenSession](../../debugger/debug-interface-access/idiadatasource-opensession.md)   
 [IDiaSession::findChildren](../../debugger/debug-interface-access/idiasession-findchildren.md)



