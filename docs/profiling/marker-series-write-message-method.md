---
title: marker_series::write_message-Methode | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- cvmarkersobj/Concurrency, diagnostic::marker_series::write_message
helpviewer_keywords:
- Concurrency, diagnostic::marker_series::write_message method
ms.assetid: 546121bc-67e0-4a5a-a456-12bd78fd6de2
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 14a4cb4a604907908b8f2b35ea0baa583ab1ca57
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "85328302"
---
# <a name="marker_serieswrite_message-method"></a>marker_series::write_message-Methode
Schreibt eine Meldung in die Ablaufverfolgungsdatei der Nebenläufigkeitsschnellansicht

## <a name="syntax"></a>Syntax

```cpp
void write_message(
   _In_ LPCTSTR _Format,
   ...
);
void write_message(
   marker_importance _Importance,
   _In_ LPCTSTR _Format,
   ...
);
void write_message(
   int _Category,
   _In_ LPCTSTR _Format,
   ...
);
void write_message(
   marker_importance _Importance,
   int _Category,
   _In_ LPCTSTR _Format,
   ...
);
```

#### <a name="parameters"></a>Parameter
 `_Format`: eine zusammengesetzte Formatzeichenfolge mit Text, der „0“ (null) oder mehr Formatelemente enthält, die Objekten in der Argumentliste entsprechen.

 `_Importance`: die Wichtigkeitsstufe.

 `_Category`: die Kategorie.

## <a name="requirements"></a>Anforderungen
 **Header:** *cvmarkersobj.h*

 **Namespace:** Concurrency::diagnostic

## <a name="see-also"></a>Siehe auch
- [marker_series-Klasse](../profiling/marker-series-class.md)