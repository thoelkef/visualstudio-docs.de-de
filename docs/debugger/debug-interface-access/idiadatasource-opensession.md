---
title: 'Idiadatasource:: OpenSession | Microsoft Docs'
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
ms.openlocfilehash: 39fe9bf3a67d3ad5f26ff7c4ccdaa9772cf1346b
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/18/2018
---
# <a name="idiadatasourceopensession"></a>IDiaDataSource::openSession
Öffnet eine Sitzung für die Abfrage von Symbolen.  
  
## <a name="syntax"></a>Syntax  
  
```C++  
HRESULT openSession (   
   IDiaSession** ppSession  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 ppSession  
 [out] Gibt eine [IDiaSession](../../debugger/debug-interface-access/idiasession.md) Objekt, das die geöffneten Sitzung darstellt.  
  
## <a name="return-value"></a>Rückgabewert  
 Im Erfolgsfall gibt `S_OK`ist, andernfalls wird ein Fehlercode zurückgegeben. Die folgende Tabelle zeigt die möglichen Rückgabewerte für diese Methode.  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|E_UNEXPECTED|Die [IDiaDataSource](../../debugger/debug-interface-access/idiadatasource.md) Objekt zuvor nicht mit der Quelle Symbole initialisiert wurde.|  
|E_INVALIDARG|Ungültige `ppSession` Parameter.|  
|E_OUTOFMEMORY|Nicht genügend Arbeitsspeicher zum Öffnen der Sitzungs.|  
  
## <a name="remarks"></a>Hinweise  
 Diese Methode öffnet ein [IDiaSession](../../debugger/debug-interface-access/idiasession.md) Objekt für eine Datenquelle.  
  
 `IDiaSession` -Objekte implementieren die Abfragen in der Datenquelle. Eine Sitzung verwaltet einen Adressraum für jeden Satz von Debugsymbolen. Ist die .exe oder .dll-Datei, die von der Quelle Datensymbole beschrieben in mehrere Adresse aktiv Bereiche (z. B., weil mehrere Prozesse geladen haben), Sie eine Sitzung für jeden-Adressbereich verwendet werden soll.  
  
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