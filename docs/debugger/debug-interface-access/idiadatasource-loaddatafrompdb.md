---
title: 'Idiadatasource:: Loaddatafrompdb | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaDataSource::loadDataFromPdb method
ms.assetid: 02159073-8144-47f8-a0b0-aa0edcb92b5b
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0cc7ce21633fc4f7cb5ad3f4dff141a7a0e46d3b
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 01/25/2019
ms.locfileid: "55023014"
---
# <a name="idiadatasourceloaddatafrompdb"></a>IDiaDataSource::loadDataFromPdb
Wird geöffnet, und bereitet eine Programmdatenbankdatei (.pdb) als Datenquelle Debuggen.  
  
## <a name="syntax"></a>Syntax  
  
```C++  
HRESULT loadDataFromPdb (  
   LPCOLESTR pdbPath  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 pdbPath  
 [in] Der Pfad zur PDB-Datei.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird `S_OK`ist, andernfalls ein Fehlercode zurückgegeben. Die folgende Tabelle zeigt die möglichen Rückgabewerte für diese Methode.  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|E_PDB_NOT_FOUND|Fehler beim Öffnen der Datei oder festgestellt, dass die Datei ein ungültiges Format aufweist.|  
|E_PDB_FORMAT|Es wurde versucht, Zugriff auf eine Datei mit der ein veraltetes Format.|  
|E_INVALIDARG|Ungültiger Parameter.|  
|E_UNEXPECTED|Die Datenquelle wurde bereits vorbereitet.|  
  
## <a name="remarks"></a>Hinweise  
 Diese Methode lädt die Debug-Daten direkt aus einer PDB-Datei.  
  
 Verwenden Sie zum Überprüfen der PDB-Datei anhand bestimmter Kriterien der [idiadatasource:: Loadandvalidatedatafrompdb](../../debugger/debug-interface-access/idiadatasource-loadandvalidatedatafrompdb.md) Methode.  
  
 Verwenden Sie für den Zugriff auf den Ladevorgang der Daten (durch einen Rückrufmechanismus bereit), die [idiadatasource:: Loaddataforexe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md) Methode.  
  
 Um eine PDB-Datei direkt aus dem Arbeitsspeicher zu laden, verwenden die [idiadatasource:: Loaddatafromistream](../../debugger/debug-interface-access/idiadatasource-loaddatafromistream.md) Methode.  
  
## <a name="example"></a>Beispiel  
  
```C++  
HRESULT hr = pSource->loadDataFromPdb( L"myprog.pdb" );  
if (FAILED(hr))  
{  
    // report error  
}  
```  
  
## <a name="see-also"></a>Siehe auch  
 [IDiaDataSource](../../debugger/debug-interface-access/idiadatasource.md)   
 [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)   
 [IDiaDataSource::loadAndValidateDataFromPdb](../../debugger/debug-interface-access/idiadatasource-loadandvalidatedatafrompdb.md)   
 [IDiaDataSource::loadDataFromIStream](../../debugger/debug-interface-access/idiadatasource-loaddatafromistream.md)