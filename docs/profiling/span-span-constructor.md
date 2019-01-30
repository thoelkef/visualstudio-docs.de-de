---
title: 'span:: span-Konstruktor | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- cvmarkersobj/Concurrency::diagnostic::span::span
helpviewer_keywords:
- Concurrency::diagnostic::span constructor
ms.assetid: 8b5578aa-5e5c-4ac7-87c7-ce87c4246e2c
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1d188f67a646d327c683125b7e59f208bdc7de61
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/25/2019
ms.locfileid: "55023209"
---
# <a name="spanspan-constructor"></a>span::span-Konstruktor
Initialisiert eine neue Instanz der `span`-Klasse.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
span(  
   const marker_series& _Series,  
   _In_ LPCTSTR _Format,  
   ...  
);  
span(  
   const marker_series& _Series,  
   marker_importance _Importance,  
   _In_ LPCTSTR _Format,  
   ...  
);  
span(  
   const marker_series& _Series,  
   int _Category,  
   _In_ LPCTSTR _Format,  
   ...  
);  
span(  
   const marker_series& _Series,  
   marker_importance _Importance,  
   int _Category,  
   _In_ LPCTSTR _Format,  
   ...  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `_Series`  
 Gültiger Markerreihenkontext.  
  
 `_Format`  
 Eine zusammengesetzte Formatzeichenfolge mit Text, der 0 oder mehr Formatelemente enthält, die Objekten in der Argumentliste entsprechen.  
  
 `_Importance`  
 Wichtigkeitsstufe.  
  
 `_Category`  
 Kategorie.  
  
## <a name="requirements"></a>Anforderungen  
 **Header:** *cvmarkersobj.h*  
  
 **Namespace:** Concurrency::diagnostic
 
 ## <a name="see-also"></a>Siehe auch
 [span-Klasse](../profiling/span-class.md)