---
title: CvIsEnabled-Funktion | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- cvmarkers/CvIsEnabledEx
- cvmarkers/CvIsEnabled
helpviewer_keywords:
- CvIsEnabled method
- CvIsEnabledEx method
ms.assetid: 2e4fea6d-758d-4150-8744-6102a1d58c1c
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8af4da802ef0ad87831f2f67f47e8ffb66a969e7
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/25/2019
ms.locfileid: "54990042"
---
# <a name="cvisenabled-function"></a>CvIsEnabled-Funktion
Ermittelt, ob der angegebene ETW-Anbieter durch eine Sitzung aktiviert wurde.  
  
## <a name="syntax"></a>Syntax  
  
```C  
HRESULT CvIsEnabled(  
   _In_ PCV_PROVIDER pProvider  
);  
HRESULT CvIsEnabledEx(  
   _In_ PCV_PROVIDER pProvider,  
   _In_ CV_IMPORTANCE level,  
   _In_ int category  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `category`  
 Kategorie.  
  
 `level`  
 Wichtigkeitsstufe.  
  
 `pProvider`  
 Gültiges Anbieterobjekt. Darf nicht NULL sein.  
  
## <a name="return-value"></a>Rückgabewert  
 S_OK, wenn der Anbieter derzeit aktiviert ist. S_FALSE, wenn der Anbieter derzeit deaktiviert ist. Fehlercode, wenn Fehler aufgetreten sind. Prüfen Sie mit dem Makro FAILED, ob Fehler vorliegen und anschließend ob S_OK/S_FALSE vorliegt.  
  
## <a name="requirements"></a>Anforderungen  
 **Header:** *cvmarkers.h*  
  
## <a name="see-also"></a>Siehe auch  
 [C++-Bibliotheksreferenz](../profiling/cpp-library-reference.md)