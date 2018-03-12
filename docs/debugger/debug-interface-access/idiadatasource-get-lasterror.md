---
title: 'Idiadatasource:: Get_lasterror | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- IDiaDataSource::get_lastError method
ms.assetid: cf08850b-8b75-4e8c-90bd-bd0214756f99
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 1a8320a78c807f08d24f6bcc41db9d775850101b
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="idiadatasourcegetlasterror"></a>IDiaDataSource::get_lastError
Ruft den Dateinamen für die letzten Ladefehler ab.  
  
## <a name="syntax"></a>Syntax  
  
```C++  
HRESULT get_lastError (  
   BSTR* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 pRetVal  
 [out] Gibt eine Zeichenfolge, die die letzten Fehler beim Laden des zugeordneten PDB-Dateinamen enthält.  
  
## <a name="return-value"></a>Rückgabewert  
 Gibt den letzten Fehlercode, der durch ein Ladevorgang verursacht. Gibt `E_INVALIDARG` Wenn die `pRetVal` Parameter ist `NULL`.  
  
## <a name="example"></a>Beispiel  
  
```C++  
BSTR    fileName;  
HRESULT errorCode = pSource->get_lastError( &fileName );  
```  
  
## <a name="see-also"></a>Siehe auch  
 [IDiaDataSource](../../debugger/debug-interface-access/idiadatasource.md)