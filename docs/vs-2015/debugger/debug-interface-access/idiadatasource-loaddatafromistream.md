---
title: 'IDiaDataSource:: loadDataFromIStream | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaDataSource::loadDataFromIStream method
ms.assetid: 8fe33eea-1457-4b8c-ae19-f1ede5578483
caps.latest.revision: 10
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 35644f06ae929e4168d5dc44d6fc488de020a637
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "62547454"
---
# <a name="idiadatasourceloaddatafromistream"></a>IDiaDataSource::loadDataFromIStream
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Bereitet die Debugdaten vor, die in einer Programm Datenbankdatei (PDB-Datei) gespeichert sind, auf die über einen Speicher internen Datenstrom zugegriffen wird  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
HRESULT loadDataFromIStream (   
   IStream* pIStream  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 pIStream  
 in Ein- <xref:IStream> Objekt, das den zu verwendenden Datenstrom darstellt.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben. In der folgenden Tabelle sind die möglichen Rückgabewerte für diese Methode aufgeführt.  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|E_PDB_FORMAT|Es wurde versucht, auf eine Datei mit einem veralteten Format zuzugreifen.|  
|E_INVALIDARG|Ungültiger Parameter.|  
|E_UNEXPECTED|Die Datenquelle wurde bereits vorbereitet.|  
  
## <a name="remarks"></a>Bemerkungen  
 Diese Methode ermöglicht das erhalten der Debugdaten für eine ausführbare Datei über ein-Objekt aus dem Arbeitsspeicher <xref:IStream> .  
  
 Wenn Sie eine PDB-Datei ohne Validierung laden möchten, verwenden Sie die [IDiaDataSource:: loadDataFromPdb](../../debugger/debug-interface-access/idiadatasource-loaddatafrompdb.md) -Methode.  
  
 Verwenden Sie die [IDiaDataSource:: loadAndValidateDataFromPdb](../../debugger/debug-interface-access/idiadatasource-loadandvalidatedatafrompdb.md) -Methode, um die PDB-Datei mit bestimmten Kriterien zu validieren.  
  
 Verwenden Sie die Methode [IDiaDataSource:: loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md) , um Zugriff auf den Daten Ladevorgang zu erhalten (über einen Rückrufmechanismus).  
  
## <a name="see-also"></a>Weitere Informationen  
 [IDiaDataSource](../../debugger/debug-interface-access/idiadatasource.md)   
 [IDiaDataSource:: loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)   
 [IDiaDataSource:: loadDataFromPdb](../../debugger/debug-interface-access/idiadatasource-loaddatafrompdb.md)   
 [IDiaDataSource::loadAndValidateDataFromPdb](../../debugger/debug-interface-access/idiadatasource-loadandvalidatedatafrompdb.md)
