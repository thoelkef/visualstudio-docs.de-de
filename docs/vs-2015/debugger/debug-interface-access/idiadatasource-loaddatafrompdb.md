---
title: 'IDiaDataSource:: loadDataFromPdb | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaDataSource::loadDataFromPdb method
ms.assetid: 02159073-8144-47f8-a0b0-aa0edcb92b5b
caps.latest.revision: 10
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 60b842e90c12d9a0bf07672380d24c8bacf71407
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68198617"
---
# <a name="idiadatasourceloaddatafrompdb"></a>IDiaDataSource::loadDataFromPdb
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Öffnet eine Programm Datenbankdatei (PDB-Datei) als debugdatenquelle und bereitet Sie vor.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
HRESULT loadDataFromPdb (  
   LPCOLESTR pdbPath  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 pdbPath  
 in Der Pfad zur PDB-Datei.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben. In der folgenden Tabelle sind die möglichen Rückgabewerte für diese Methode aufgeführt.  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|E_PDB_NOT_FOUND|Die Datei konnte nicht geöffnet werden, oder es wurde festgestellt, dass die Datei ein ungültiges Format aufweist.|  
|E_PDB_FORMAT|Es wurde versucht, auf eine Datei mit einem veralteten Format zuzugreifen.|  
|E_INVALIDARG|Ungültiger Parameter.|  
|E_UNEXPECTED|Die Datenquelle wurde bereits vorbereitet.|  
  
## <a name="remarks"></a>Bemerkungen  
 Diese Methode lädt die Debugdaten direkt aus einer PDB-Datei.  
  
 Verwenden Sie die [IDiaDataSource:: loadAndValidateDataFromPdb](../../debugger/debug-interface-access/idiadatasource-loadandvalidatedatafrompdb.md) -Methode, um die PDB-Datei mit bestimmten Kriterien zu validieren.  
  
 Verwenden Sie die Methode [IDiaDataSource:: loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md) , um Zugriff auf den Daten Ladevorgang zu erhalten (über einen Rückrufmechanismus).  
  
 Verwenden Sie die [IDiaDataSource:: loadDataFromIStream](../../debugger/debug-interface-access/idiadatasource-loaddatafromistream.md) -Methode, um eine PDB-Datei direkt aus dem Arbeitsspeicher zu laden.  
  
## <a name="example"></a>Beispiel  
  
```cpp#  
HRESULT hr = pSource->loadDataFromPdb( L"myprog.pdb" );  
if (FAILED(hr))  
{  
    // report error  
}  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [IDiaDataSource](../../debugger/debug-interface-access/idiadatasource.md)   
 [IDiaDataSource:: loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)   
 [IDiaDataSource:: loadAndValidateDataFromPdb](../../debugger/debug-interface-access/idiadatasource-loadandvalidatedatafrompdb.md)   
 [IDiaDataSource::loadDataFromIStream](../../debugger/debug-interface-access/idiadatasource-loaddatafromistream.md)
