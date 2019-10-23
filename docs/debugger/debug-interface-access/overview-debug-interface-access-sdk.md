---
title: Übersicht (Debug Interface Access SDK) | Microsoft-Dokumentation
ms.date: 11/04/2016
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1e4269c620247f256d2cfae2e84b76ff60fcf9ba
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/22/2019
ms.locfileid: "72738605"
---
# <a name="overview-debug-interface-access-sdk"></a>Übersicht (Debug Interface Access SDK)
Verwenden Sie die Dia SDK, um auf die Microsoft-Debuginformationen zuzugreifen. Der DIA SDK stellt einen com-basierten API-Satz bereit, der die Notwendigkeit zum Umschreiben des Codes überflüssig macht, wenn Microsoft das Format der Debuginformationen ändert. Mit dem Dia SDK können Sie auch aus einem ausgewählten Satz vorheriger Versionen von Debuginformationen lesen, die sich in PDB-und dbg-Dateien befinden, die von [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] Versionen 5,0 und höher generiert werden.

 Jede Schnittstelle im Dia SDK stellt ein anderes com-Objekt dar, außer wenn anders angegeben. Zusätzliche Schnittstellen und somit zusätzliche Objekte werden mithilfe von expliziten Abfragen, wie z. b. [IDiaDataSource:: OpenSession](../../debugger/debug-interface-access/idiadatasource-opensession.md) oder [IDiaSession:: findChildren](../../debugger/debug-interface-access/idiasession-findchildren.md), erstellt, anstatt `QueryInterface` für vorhandene Schnittstellen Zeiger Aufrufs.

## <a name="see-also"></a>Siehe auch
- [IDiaDataSource::openSession](../../debugger/debug-interface-access/idiadatasource-opensession.md)
- [IDiaSession::findChildren](../../debugger/debug-interface-access/idiasession-findchildren.md)