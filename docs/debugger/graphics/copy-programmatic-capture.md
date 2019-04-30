---
title: Kopieren (programmgesteuerte Aufzeichnung) | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 30ec235a-0abb-44b9-8852-61bc9e67ce22
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3a888605cfae6b5430782defd198f83988c31870
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62895953"
---
# <a name="copy-programmatic-capture"></a>Kopieren (Programmgesteuerte Aufzeichnung)
Kopiert den Inhalt der aktiven Grafikprotokolldatei (VSGLOG) in eine neue Datei.

## <a name="syntax"></a>Syntax

```C++
void Copy(
  wchar_t const * szNewVSGLog
);
```

#### <a name="parameters"></a>Parameter
 `szNewVSGLog` Der Dateiname der neuen Grafikprotokolldatei.

## <a name="remarks"></a>Hinweise
 Um die Grafikinformationen in eine neuen Datei zu kopieren, müssen Sie bereits einige Grafikinformationen erfasst haben, andernfalls geschieht nichts.