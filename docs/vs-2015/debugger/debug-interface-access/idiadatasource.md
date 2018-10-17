---
title: IDiaDataSource | Microsoft-Dokumentation
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
- IDiaDataSource interface
ms.assetid: 6260ac76-4f9d-4144-ba22-32f8620b32c2
caps.latest.revision: 16
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2abe262ee42d1a22e37e60446f3c44581e40078c
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2018
ms.locfileid: "49249651"
---
# <a name="idiadatasource"></a>IDiaDataSource
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Initiiert den Zugriff auf eine Quelle für die Debugsymbole.  
  
## <a name="syntax"></a>Syntax  
  
```  
IDiaDataSource : IUnknown  
```  
  
## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge  
 Die folgende Tabelle zeigt die Methoden der `IDiaDataSource`.  
  
|Methode|Beschreibung|  
|------------|-----------------|  
|[IDiaDataSource::get_lastError](../../debugger/debug-interface-access/idiadatasource-get-lasterror.md)|Ruft den Dateinamen für die letzten Ladefehler ab.|  
|[IDiaDataSource::loadDataFromPdb](../../debugger/debug-interface-access/idiadatasource-loaddatafrompdb.md)|Wird geöffnet, und bereitet eine Programmdatenbankdatei (.pdb) als Datenquelle Debuggen.|  
|[IDiaDataSource::loadAndValidateDataFromPdb](../../debugger/debug-interface-access/idiadatasource-loadandvalidatedatafrompdb.md)|Wird geöffnet und überprüft, ob die Programmdatenbankdatei (.pdb) der bereitgestellten Signaturinformationen übereinstimmt; Bereitet die PDB-Datei als Datenquelle Debuggen.|  
|[IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)|Wird geöffnet, und bereitet die Debug-Daten, die der Datei.exe/.dll zugeordnet.|  
|[IDiaDataSource::loadDataFromIStream](../../debugger/debug-interface-access/idiadatasource-loaddatafromistream.md)|Bereitet die Debug-Daten in ein Zugriff erfolgt über einen in-Memory-Datenstrom Programmdatenbankdatei (PDB) gespeichert.|  
|[IDiaDataSource::openSession](../../debugger/debug-interface-access/idiadatasource-opensession.md)|Wird eine Sitzung für das Abfragen von Symbolen geöffnet.|  
  
## <a name="remarks"></a>Hinweise  
 Aufrufen einer der Load-Methoden von der `IDiaDataSource` Schnittstelle öffnet die Symbol-Quelle. Einem erfolgreichen Aufruf der [idiadatasource:: OpenSession](../../debugger/debug-interface-access/idiadatasource-opensession.md) Methode gibt ein [IDiaSession](../../debugger/debug-interface-access/idiasession.md) -Schnittstelle, die Abfragen der Datenquelle unterstützt. Wenn die Load-Methode einen Datei-bezogener Fehler zurückgibt und dann die [idiadatasource:: Get_lasterror](../../debugger/debug-interface-access/idiadatasource-get-lasterror.md) Methodenrückgabewert Wert enthält den Dateinamen, die dem Fehler zugeordnet.  
  
## <a name="notes-for-callers"></a>Hinweise für Aufrufer  
 Diese Schnittstelle wird abrufen durch Aufrufen der `CoCreateInstance` -Funktion mit den Klassenbezeichner `CLSID_DiaSource` und die Schnittstellen-ID des `IID_IDiaDataSource`. Im Beispiel wird gezeigt, wie diese Schnittstelle abgerufen wird.  
  
## <a name="example"></a>Beispiel  
  
```cpp#  
  
      IDiaDataSource* pSource;  
HRESULT hr = CoCreateInstance(CLSID_DiaSource,  
                              NULL,  
                              CLSCTX_INPROC_SERVER,  
                              IID_IDiaDataSource,  
                              (void**) &pSource);  
if (FAILED(hr))  
{  
    // Report error and exit  
}  
```  
  
## <a name="requirements"></a>Anforderungen  
 Header: Dia2.h  
  
 Bibliothek: diaguids.lib  
  
 DLL: "MSDIA80.dll"  
  
## <a name="see-also"></a>Siehe auch  
 [Schnittstellen (Debug Interface Access SDK)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)



