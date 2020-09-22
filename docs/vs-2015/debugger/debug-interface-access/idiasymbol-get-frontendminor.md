---
title: IDiaSymbol::get_frontEndMinor | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_frontEndMinor method
ms.assetid: 40792153-827c-4859-be7c-6aa16d5abab6
caps.latest.revision: 12
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 12e5956f880a79d7946ff9655ec1ef3d1a79ff22
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "90841104"
---
# <a name="idiasymbolget_frontendminor"></a>IDiaSymbol::get_frontEndMinor
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Ruft die neben Versionsnummer des Front-Ends ab.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
HRESULT get_frontEndMinor (   
   DWORD* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pRetVal`  
 vorgenommen Gibt die neben Versionsnummer von Front. End zurück.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird zurückgegeben `S_OK` ; andernfalls wird der- `S_FALSE` oder-Fehlercode zurückgegeben.  
  
> [!NOTE]
> Der Rückgabewert `S_FALSE` bedeutet, dass die Eigenschaft für das Symbol nicht verfügbar ist.  
  
## <a name="remarks"></a>Bemerkungen  
 Ein Compiler besteht in der Regel aus zwei primären Elementen: dem Front-End (dem Parser), das die Analyse des Quellcodes in ein zwischen Formular und ein Back-End (Code Generator) behandelt, das das zwischen Formular in eine Assembly konvertiert. Es ist nicht ungewöhnlich, dass das Front-End eine andere Version als das Back-End hat.  
  
 Eine Front-End-oder Back-End-Versionsnummer besteht aus drei Teilen: \<major> . \<minor> . \<build> , wobei \<major> die Hauptversionsnummer, \<minor> die neben Versionsnummer und \<build> die Buildnummer ist. Beispiel: 13.10.3077.  
  
## <a name="requirements"></a>Anforderungen  
  
|Anforderung|BESCHREIBUNG|  
|-----------------|-----------------|  
|Header:|dia2.h|  
|Version:|Dia SDK v 7.0|  
  
## <a name="see-also"></a>Weitere Informationen  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
