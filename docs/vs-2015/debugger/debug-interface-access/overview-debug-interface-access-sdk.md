---
title: Übersicht (Debug Interface Access SDK) | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
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
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 7374b03da42e34e8ac3be8c7cc570769d9cfd1ff
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68179210"
---
# <a name="overview-debug-interface-access-sdk"></a>Übersicht (Debug Interface Access SDK)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Verwenden Sie die Dia SDK, um auf die Microsoft-Debuginformationen zuzugreifen. Der DIA SDK stellt einen com-basierten API-Satz bereit, der die Notwendigkeit zum Umschreiben des Codes überflüssig macht, wenn Microsoft das Format der Debuginformationen ändert. Mit dem Dia SDK können Sie auch aus einem ausgewählten Satz vorheriger Versionen von Debuginformationen lesen, die sich in PDB-und dbg-Dateien befinden, die von den [!INCLUDE[vcprvc](../../includes/vcprvc-md.md)] Versionen 5,0 und höher generiert wurden.  
  
 Jede Schnittstelle im Dia SDK stellt ein anderes com-Objekt dar, außer wenn anders angegeben. Zusätzliche Schnittstellen und somit zusätzliche Objekte werden mithilfe von expliziten Abfragen, wie z. b. [IDiaDataSource:: OpenSession](../../debugger/debug-interface-access/idiadatasource-opensession.md) oder [IDiaSession:: findChildren](../../debugger/debug-interface-access/idiasession-findchildren.md), erstellt, nicht durch Aufrufen von `QueryInterface` für vorhandene Schnittstellen Zeiger.  
  
## <a name="see-also"></a>Weitere Informationen  
 [IDiaDataSource:: OpenSession](../../debugger/debug-interface-access/idiadatasource-opensession.md)   
 [IDiaSession::findChildren](../../debugger/debug-interface-access/idiasession-findchildren.md)
