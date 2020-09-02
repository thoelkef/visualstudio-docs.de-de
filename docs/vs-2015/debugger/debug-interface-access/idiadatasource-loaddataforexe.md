---
title: 'IDiaDataSource:: loadDataForExe | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaDataSource::loadDataForExe method
ms.assetid: d94a1068-f53f-44b5-b6fb-00dec361a7f2
caps.latest.revision: 15
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 623cdd74b086a46bc52c0f0534953ae6e11168ff
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "62547376"
---
# <a name="idiadatasourceloaddataforexe"></a>IDiaDataSource::loadDataForExe
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Öffnet und bereitet die der exe-/dll-Datei zugeordneten Debugdaten vor.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
HRESULT loadDataForExe (  
   LPCOLESTR executable,  
   LPCOLESTR searchPath,  
   IUnknown* pCallback  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 executable  
 in Pfad zur exe-oder DLL-Datei.  
  
 searchPath  
 in Alternativer Pfad für die Suche nach Debugdaten.  
  
 pCallback  
 in Eine `IUnknown` Schnittstelle für ein Objekt, das eine Debug-Rückruf Schnittstelle unterstützt, wie z. b. die Schnittstellen [IDiaLoadCallback](../../debugger/debug-interface-access/idialoadcallback.md), [IDiaLoadCallback2](../../debugger/debug-interface-access/idialoadcallback2.md), [IDiaReadExeAtOffsetCallback](../../debugger/debug-interface-access/idiareadexeatoffsetcallback.md)und/oder [IDiaReadExeAtRVACallback](../../debugger/debug-interface-access/idiareadexeatrvacallback.md) .  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben. In der folgenden Tabelle werden einige der möglichen Fehlercodes für diese Methode aufgeführt.  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|E_PDB_NOT_FOUND|Die Datei konnte nicht geöffnet werden, oder die Datei weist ein ungültiges Format auf.|  
|E_PDB_FORMAT|Es wurde versucht, auf eine Datei mit einem veralteten Format zuzugreifen.|  
|E_PDB_INVALID_SIG|Signatur stimmt nicht mit ab.|  
|E_PDB_INVALID_AGE|Das Alter stimmt nicht mit.|  
|E_INVALIDARG|Ungültiger Parameter.|  
|E_UNEXPECTED|Die Datenquelle wurde bereits vorbereitet.|  
  
## <a name="remarks"></a>Bemerkungen  
 Der Debug-Header der exe-/dll-Datei benennt den zugeordneten Speicherort der Debugdaten.  
  
 Diese Methode liest den Debug-Header und sucht dann nach den Debugdaten und bereitet Sie vor. Der Fortschritt der Suche kann optional über Rückrufe gemeldet und gesteuert werden. Beispielsweise wird [IDiaLoadCallback:: NotifyDebugDir](../../debugger/debug-interface-access/idialoadcallback-notifydebugdir.md) aufgerufen, wenn die `IDiaDataSource::loadDataForExe` -Methode ein Debugverzeichnis findet und verarbeitet.  
  
 Mithilfe der [IDiaReadExeAtOffsetCallback](../../debugger/debug-interface-access/idiareadexeatoffsetcallback.md) -Schnittstelle und der [IDiaReadExeAtRVACallback](../../debugger/debug-interface-access/idiareadexeatrvacallback.md) -Schnittstelle kann die Client Anwendung Alternative Methoden zum Lesen von Daten aus der ausführbaren Datei bereitstellen, wenn nicht direkt über Standarddatei-e/a auf die Datei zugegriffen werden kann.  
  
 Wenn Sie eine PDB-Datei ohne Validierung laden möchten, verwenden Sie die [IDiaDataSource:: loadDataFromPdb](../../debugger/debug-interface-access/idiadatasource-loaddatafrompdb.md) -Methode.  
  
 Verwenden Sie die [IDiaDataSource:: loadAndValidateDataFromPdb](../../debugger/debug-interface-access/idiadatasource-loadandvalidatedatafrompdb.md) -Methode, um die PDB-Datei mit bestimmten Kriterien zu validieren.  
  
 Verwenden Sie die [IDiaDataSource:: loadDataFromIStream](../../debugger/debug-interface-access/idiadatasource-loaddatafromistream.md) -Methode, um eine PDB-Datei direkt aus dem Arbeitsspeicher zu laden.  
  
## <a name="example"></a>Beispiel  
  
```cpp#  
class MyCallBack: public IDiaLoadCallback  
{  
...  
};  
MyCallBack callback;  
...  
HRESULT hr = pSource->loadDataForExe( L"myprog.exe", L".\debug", (IUnknown*)&callback);  
if (FAILED(hr))  
{  
    // Report error  
}  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [IDiaDataSource](../../debugger/debug-interface-access/idiadatasource.md)   
 [IDiaLoadCallback](../../debugger/debug-interface-access/idialoadcallback.md)   
 [IDiaLoadCallback2](../../debugger/debug-interface-access/idialoadcallback2.md)   
 [IDiaLoadCallback:: notifydebug-dir](../../debugger/debug-interface-access/idialoadcallback-notifydebugdir.md)   
 [IDiaReadExeAtOffsetCallback](../../debugger/debug-interface-access/idiareadexeatoffsetcallback.md)   
 [IDiaReadExeAtRVACallback](../../debugger/debug-interface-access/idiareadexeatrvacallback.md)   
 [IDiaDataSource:: loadDataFromPdb](../../debugger/debug-interface-access/idiadatasource-loaddatafrompdb.md)   
 [IDiaDataSource:: loadAndValidateDataFromPdb](../../debugger/debug-interface-access/idiadatasource-loadandvalidatedatafrompdb.md)   
 [IDiaDataSource::loadDataFromIStream](../../debugger/debug-interface-access/idiadatasource-loaddatafromistream.md)
