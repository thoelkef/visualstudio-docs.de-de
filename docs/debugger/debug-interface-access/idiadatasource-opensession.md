---
title: 'Idiadatasource:: OpenSession | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaDataSource::openSession method
ms.assetid: a3319ed0-3979-483b-9852-c0af96852c48
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 8266102e8bc2c347ed8a554a3c64d9504f1e863b
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49933507"
---
# <a name="idiadatasourceopensession"></a>IDiaDataSource::openSession
Wird eine Sitzung für das Abfragen von Symbolen geöffnet.  
  
## <a name="syntax"></a>Syntax  
  
```C++  
HRESULT openSession (   
   IDiaSession** ppSession  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 ppSession  
 [out] Gibt eine [IDiaSession](../../debugger/debug-interface-access/idiasession.md) Objekt, das die geöffnete Sitzung darstellt.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird `S_OK`ist, andernfalls ein Fehlercode zurückgegeben. Die folgende Tabelle zeigt die möglichen Rückgabewerte für diese Methode.  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|E_UNEXPECTED|Die [IDiaDataSource](../../debugger/debug-interface-access/idiadatasource.md) Objekt zuvor nicht mit der Quelle von Symbolen initialisiert wurde.|  
|E_INVALIDARG|Ungültige `ppSession` Parameter.|  
|E_OUTOFMEMORY|Nicht genügend Arbeitsspeicher, um die Sitzung zu öffnen.|  
  
## <a name="remarks"></a>Hinweise  
 Diese Methode öffnet ein [IDiaSession](../../debugger/debug-interface-access/idiasession.md) Objekt für eine Datenquelle.  
  
 `IDiaSession` Objekte werden Abfragen in der Datenquelle implementieren. Eine Sitzung verwaltet einen Adressraum für jeden Satz von Debugsymbolen. Wenn die .exe oder .dll-Datei, die von der Quelle Datensymbole beschrieben ist in mehrere Adressen aktiv Bereichen (z. B., weil mehrere Prozesse geladen haben), und dann eine Sitzung für jeden Adressbereich verwendet werden soll.  
  
## <a name="example"></a>Beispiel  
  
```C++  
IDiaSession* pSession;  
HRESULT hr = pSource->openSession( &pSession );  
if (FAILED(hr))  
{  
   // report error  
}  
```  
  
## <a name="see-also"></a>Siehe auch  
 [IDiaDataSource](../../debugger/debug-interface-access/idiadatasource.md)   
 [Übersicht](../../debugger/debug-interface-access/overview-debug-interface-access-sdk.md)   
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)   
 [Abfragen der PDB-Datei](../../debugger/debug-interface-access/querying-the-dot-pdb-file.md)