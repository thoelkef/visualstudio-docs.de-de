---
title: marker_series::is_enabled-Methode | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- cvmarkersobj/Concurrency::diagnostic::marker_series::is_enabled
helpviewer_keywords:
- Concurrency::diagnostic::marker_series::is_enabled method
ms.assetid: 8ce4dd50-ca29-4c72-98d6-582693f7d501
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 22a7baa08a29cd77506e48762179118b3bbb2d1a
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/21/2019
ms.locfileid: "56639933"
---
# <a name="markerseriesisenabled-method"></a>marker_series:: is_enabled-Methode
Bestimmt, ob eine Sitzung den Anbieter aktiviert hat

## <a name="syntax"></a>Syntax

```cpp
bool is_enabled();
bool is_enabled(
   marker_importance _Importance,
   int _Category
);
```

#### <a name="parameters"></a>Parameter
 `_Importance`: die Wichtigkeitsstufe.

 `_Category`: die Kategorie.

## <a name="return-value"></a>Rückgabewert

## <a name="requirements"></a>Anforderungen
 **Header:** *cvmarkersobj.h*

 **Namespace:** Concurrency::diagnostic

## <a name="see-also"></a>Siehe auch
- [marker_series-Klasse](../profiling/marker-series-class.md)