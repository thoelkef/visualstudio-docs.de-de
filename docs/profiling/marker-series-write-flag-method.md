---
title: marker_series::write_flag-Methode | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- cvmarkersojb/Concurrency::diagnostic::marker_series::write_flag
helpviewer_keywords:
- Concurrency::diagnostic::marker_series::write_flag method
ms.assetid: ca07f388-e5d5-46fd-b991-fe6e9029a68f
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f09cca9bd1e3babccb0debc369881a0efa00fa0b
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/21/2019
ms.locfileid: "56625113"
---
# <a name="markerserieswriteflag-method"></a>marker_series::write_flag-Methode
Schreibt ein Flag in die Ablaufverfolgungsdatei der Nebenläufigkeitsschnellansicht

## <a name="syntax"></a>Syntax

```cpp
void write_flag(
   _In_ LPCTSTR _Format,
   ...
);
void write_flag(
   marker_importance _Importance,
   _In_ LPCTSTR _Format,
   ...
);
void write_flag(
   int _Category,
   _In_ LPCTSTR _Format,
   ...
);
void write_flag(
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