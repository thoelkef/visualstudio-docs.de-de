---
title: CvIsEnabled-Funktion | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- cvmarkers/CvIsEnabledEx
- cvmarkers/CvIsEnabled
helpviewer_keywords:
- CvIsEnabled method
- CvIsEnabledEx method
ms.assetid: 2e4fea6d-758d-4150-8744-6102a1d58c1c
caps.latest.revision: 8
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: ba30f3ab75504c0115b8a881f2014910f3b9fd0b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68177777"
---
# <a name="cvisenabled-function"></a>CvIsEnabled-Funktion
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Ermittelt, ob der angegebene ETW-Anbieter durch eine Sitzung aktiviert wurde.  
  
## <a name="syntax"></a>Syntax  
  
```  
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
 **Header:** cvmarkers.h  
  
## <a name="see-also"></a>Weitere Informationen  
 [C++-Bibliotheks Referenz](../profiling/cpp-library-reference.md)
