---
title: 'Idiadatasource:: Loaddatafromistream | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaDataSource::loadDataFromIStream method
ms.assetid: 8fe33eea-1457-4b8c-ae19-f1ede5578483
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 2421e25c51d005a069de316d1d465eca80a0432b
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/18/2018
---
# <a name="idiadatasourceloaddatafromistream"></a>IDiaDataSource::loadDataFromIStream
Bereitet die Debugdaten in ein Zugriff erfolgt über ein in-Memory-Datenstrom Programmdatenbankdatei (PDB) gespeichert.  
  
## <a name="syntax"></a>Syntax  
  
```C++  
HRESULT loadDataFromIStream (   
   IStream* pIStream  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 pIStream  
 [in] Ein <xref:IStream> Objekt, das den Datenstrom mit darstellt.  
  
## <a name="return-value"></a>Rückgabewert  
 Im Erfolgsfall gibt `S_OK`ist, andernfalls wird ein Fehlercode zurückgegeben. Die folgende Tabelle zeigt die möglichen Rückgabewerte für diese Methode.  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|E_PDB_FORMAT|Es wurde versucht, Zugriff auf eine Datei mit der ein veraltetes Format.|  
|E_INVALIDARG|Invalidparameter.|  
|E_UNEXPECTED|Die Datenquelle wurde bereits vorbereitet wurde.|  
  
## <a name="remarks"></a>Hinweise  
 Diese Methode ermöglicht die Debugdaten für eine ausführbare Datei aus dem Arbeitsspeicher über abgerufen werden soll ein <xref:IStream> Objekt.  
  
 Verwenden Sie zum Laden einer PDB-Datei ohne Überprüfung der [idiadatasource:: Loaddatafrompdb](../../debugger/debug-interface-access/idiadatasource-loaddatafrompdb.md) Methode.  
  
 Verwenden Sie zum Überprüfen der PDB-Datei anhand bestimmter Kriterien die [idiadatasource:: Loadandvalidatedatafrompdb](../../debugger/debug-interface-access/idiadatasource-loadandvalidatedatafrompdb.md) Methode.  
  
 Verwenden Sie zum Laden von Daten (durch einen Rückrufmechanismus) Zugriff auf die [idiadatasource:: Loaddataforexe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md) Methode.  
  
## <a name="see-also"></a>Siehe auch  
 [IDiaDataSource](../../debugger/debug-interface-access/idiadatasource.md)   
 [Idiadatasource:: Loaddataforexe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)   
 [Idiadatasource:: Loaddatafrompdb](../../debugger/debug-interface-access/idiadatasource-loaddatafrompdb.md)   
 [IDiaDataSource::loadAndValidateDataFromPdb](../../debugger/debug-interface-access/idiadatasource-loadandvalidatedatafrompdb.md)