---
title: Übersicht (Debug Interface Access SDK) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
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
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 807690edaf5626e3ec007a005717622592c14ce9
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/18/2018
ms.locfileid: "31471439"
---
# <a name="overview-debug-interface-access-sdk"></a>Übersicht (Debug Interface Access SDK)
Verwenden Sie das DIA SDK Zugriff auf die Microsoft-Debuginformationen. Das DIA SDK bietet eine COM-API-Satz basierte, die entfällt die Notwendigkeit, den Code umschreiben, wenn Microsoft das Format der Debuginformationen ändert. Das DIA SDK können Sie gelesen werden, einen ausgewählten Satz von früheren Versionen von Debuginformationen, befindet sich in der PDB-Datei und .dbg-Dateien generiert werden auch [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] Versionen 5.0 und höher.  
  
 Jede Schnittstelle in DIA-SDK stellt ein anderen COM-Objekt, mit Ausnahme dar, sofern nichts anderes angegeben ist. Weitere Schnittstellen und somit zusätzliche Objekte erstellt mithilfe von Abfragen im explicit, z. B. [idiadatasource:: OpenSession](../../debugger/debug-interface-access/idiadatasource-opensession.md) oder [idiasession:: Findchildren](../../debugger/debug-interface-access/idiasession-findchildren.md), statt durch Aufrufen von `QueryInterface` auf vorhandene Schnittstellenzeiger.  
  
## <a name="see-also"></a>Siehe auch  
 [Idiadatasource:: OpenSession](../../debugger/debug-interface-access/idiadatasource-opensession.md)   
 [IDiaSession::findChildren](../../debugger/debug-interface-access/idiasession-findchildren.md)