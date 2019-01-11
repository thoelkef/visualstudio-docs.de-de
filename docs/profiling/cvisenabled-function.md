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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 0c35fc883e53e1b1cc430724d87d8bcbd1bb32ee
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/02/2019
ms.locfileid: "53989188"
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