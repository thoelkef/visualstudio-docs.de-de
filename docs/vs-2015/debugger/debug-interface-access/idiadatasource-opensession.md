---
title: 'IDiaDataSource:: OpenSession | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaDataSource::openSession method
ms.assetid: a3319ed0-3979-483b-9852-c0af96852c48
caps.latest.revision: 10
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 4bec5507d15374e6e88afd4567d4b0fec9ca6cb7
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68198598"
---
# <a name="idiadatasourceopensession"></a>IDiaDataSource::openSession
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Öffnet eine Sitzung zum Abfragen von Symbolen.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
HRESULT openSession (   
   IDiaSession** ppSession  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 ppSession  
 vorgenommen Gibt ein [IDiaSession](../../debugger/debug-interface-access/idiasession.md) -Objekt zurück, das die geöffnete Sitzung darstellt.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben. In der folgenden Tabelle sind die möglichen Rückgabewerte für diese Methode aufgeführt.  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|E_UNEXPECTED|Das [IDiaDataSource](../../debugger/debug-interface-access/idiadatasource.md) -Objekt wurde zuvor nicht mit einer Quelle von Symbolen initialisiert.|  
|E_INVALIDARG|Ungültiger `ppSession`-Parameter.|  
|E_OUTOFMEMORY|Nicht genügend Arbeitsspeicher zum Öffnen der Sitzung.|  
  
## <a name="remarks"></a>Bemerkungen  
 Diese Methode öffnet ein [IDiaSession](../../debugger/debug-interface-access/idiasession.md) -Objekt für eine Datenquelle.  
  
 `IDiaSession` -Objekte implementieren Abfragen in der Datenquelle. Eine Sitzung verwaltet einen Adressraum für jeden Satz von Debugsymbolen. Wenn die exe-oder DLL-Datei, die von den Datenquellen Symbolen beschrieben wird, in mehreren Adressbereichen aktiv ist (z. b. weil Sie von mehreren Prozessen geladen wurde), sollte eine Sitzung für jeden Adressbereich verwendet werden.  
  
## <a name="example"></a>Beispiel  
  
```cpp#  
IDiaSession* pSession;  
HRESULT hr = pSource->openSession( &pSession );  
if (FAILED(hr))  
{  
   // report error  
}  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [IDiaDataSource](../../debugger/debug-interface-access/idiadatasource.md)   
 [Übersicht über](../../debugger/debug-interface-access/overview-debug-interface-access-sdk.md)   
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)   
 [Abfragen der PDB-Datei](../../debugger/debug-interface-access/querying-the-dot-pdb-file.md)
