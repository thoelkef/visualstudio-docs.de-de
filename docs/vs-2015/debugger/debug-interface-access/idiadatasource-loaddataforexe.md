---
title: 'Idiadatasource:: Loaddataforexe | Microsoft-Dokumentation'
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
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2019
ms.locfileid: "58958223"
---
# <a name="idiadatasourceloaddataforexe"></a>IDiaDataSource::loadDataForExe
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Wird geöffnet, und bereitet die Debug-Daten, die der Datei.exe/.dll zugeordnet.  
  
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
 [in] Pfad zur .exe oder .dll-Datei.  
  
 searchPath  
 [in] Alternativen Pfad für die Debug-Daten zu suchen.  
  
 pCallback  
 [in] Ein `IUnknown` Schnittstelle für ein Objekt, das eine Debug-Rückrufschnittstelle,, z. B. unterstützt die [IDiaLoadCallback](../../debugger/debug-interface-access/idialoadcallback.md), [IDiaLoadCallback2](../../debugger/debug-interface-access/idialoadcallback2.md), [IDiaReadExeAtOffsetCallback](../../debugger/debug-interface-access/idiareadexeatoffsetcallback.md), bzw. die [IDiaReadExeAtRVACallback](../../debugger/debug-interface-access/idiareadexeatrvacallback.md) Schnittstellen.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird `S_OK`ist, andernfalls ein Fehlercode zurückgegeben. Die folgende Tabelle zeigt einige der möglichen Fehlercodes für diese Methode.  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|E_PDB_NOT_FOUND|Fehler beim Öffnen der Datei, oder die Datei weist ein ungültiges Format.|  
|E_PDB_FORMAT|Es wurde versucht, Zugriff auf eine Datei mit der ein veraltetes Format.|  
|E_PDB_INVALID_SIG|Signatur stimmt nicht überein.|  
|E_PDB_INVALID_AGE|Alter stimmt nicht überein.|  
|E_INVALIDARG|Ungültiger Parameter.|  
|E_UNEXPECTED|Die Datenquelle wurde bereits vorbereitet.|  
  
## <a name="remarks"></a>Hinweise  
 Die debugheader der Datei.exe/.dll benennt den Speicherort der zugeordneten Debuggen.  
  
 Diese Methode liest den debugheader und sucht dann nach und bereitet die Debug-Daten. Der Status der Suche kann optional gemeldet und durch Rückrufe gesteuert werden. Z. B. die [idialoadcallback:: Notifydebugdir](../../debugger/debug-interface-access/idialoadcallback-notifydebugdir.md) wird aufgerufen, wenn die `IDiaDataSource::loadDataForExe` Methode findet und ein Debugverzeichnis verarbeitet.  
  
 Die [IDiaReadExeAtOffsetCallback](../../debugger/debug-interface-access/idiareadexeatoffsetcallback.md) und [IDiaReadExeAtRVACallback](../../debugger/debug-interface-access/idiareadexeatrvacallback.md) Schnittstellen können von der Clientanwendung, geben Sie alternative Methoden zum Lesen von Daten aus der ausführbaren Datei Datei, wenn die Datei kann nicht direkt über standard-Datei-e/a zugegriffen werden.  
  
 Verwenden Sie zum Laden einer PDB-Datei ohne Überprüfung der [idiadatasource:: Loaddatafrompdb](../../debugger/debug-interface-access/idiadatasource-loaddatafrompdb.md) Methode.  
  
 Verwenden Sie zum Überprüfen der PDB-Datei anhand bestimmter Kriterien der [idiadatasource:: Loadandvalidatedatafrompdb](../../debugger/debug-interface-access/idiadatasource-loadandvalidatedatafrompdb.md) Methode.  
  
 Um eine PDB-Datei direkt aus dem Arbeitsspeicher zu laden, verwenden die [idiadatasource:: Loaddatafromistream](../../debugger/debug-interface-access/idiadatasource-loaddatafromistream.md) Methode.  
  
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
  
## <a name="see-also"></a>Siehe auch  
 [IDiaDataSource](../../debugger/debug-interface-access/idiadatasource.md)   
 [IDiaLoadCallback](../../debugger/debug-interface-access/idialoadcallback.md)   
 [IDiaLoadCallback2](../../debugger/debug-interface-access/idialoadcallback2.md)   
 [IDiaLoadCallback::NotifyDebugDir](../../debugger/debug-interface-access/idialoadcallback-notifydebugdir.md)   
 [IDiaReadExeAtOffsetCallback](../../debugger/debug-interface-access/idiareadexeatoffsetcallback.md)   
 [IDiaReadExeAtRVACallback](../../debugger/debug-interface-access/idiareadexeatrvacallback.md)   
 [IDiaDataSource::loadDataFromPdb](../../debugger/debug-interface-access/idiadatasource-loaddatafrompdb.md)   
 [IDiaDataSource::loadAndValidateDataFromPdb](../../debugger/debug-interface-access/idiadatasource-loadandvalidatedatafrompdb.md)   
 [IDiaDataSource::loadDataFromIStream](../../debugger/debug-interface-access/idiadatasource-loaddatafromistream.md)
