---
title: 'Idiadatasource:: OpenSession | Microsoft-Dokumentation'
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
- IDiaDataSource::openSession method
ms.assetid: a3319ed0-3979-483b-9852-c0af96852c48
caps.latest.revision: 10
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 79c3ec1974341ddee0a147830491bf324b1fe0c5
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/16/2018
ms.locfileid: "51769844"
---
# <a name="idiadatasourceopensession"></a>IDiaDataSource::openSession
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Wird eine Sitzung für das Abfragen von Symbolen geöffnet.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
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
  
```cpp#  
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



