---
title: marker_series -Klasse | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- cvmarkersobj/Concurrency::diagnostic::marker_series
helpviewer_keywords:
- Concurrency::diagnostic::marker_series class
ms.assetid: b8445ed0-c512-4f92-b6b4-3d05c044f939
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 075a81dc81bb202be913f5a06e8213a8a68a010f
ms.sourcegitcommit: 046a9adc5fa6d6d05157204f5fd1a291d89760b7
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/11/2018
---
# <a name="markerseries-class"></a>marker_series-Klasse
Stellt einen seriellen Kanal mit Ereignissen dar, die von einem einzelnen Anbieter generiert werden.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
class marker_series;  
```  
  
## <a name="members"></a>Member  
  
### <a name="public-constructors"></a>Öffentliche Konstruktoren  
  
|name|description|  
|----------|-----------------|  
|[marker_series::marker_series-Konstruktor](../profiling/marker-series-marker-series-constructor.md)|Initialisiert eine neue Instanz der `marker_series`-Klasse.|  
|[marker_series::~marker_series-Destruktor](../profiling/marker-series-tilde-marker-series-destructor.md)|Zerstört das marker_series-Objekt und gibt alle zugewiesenen Ressourcen frei|  
  
### <a name="public-methods"></a>Öffentliche Methoden  
  
|name|description|  
|----------|-----------------|  
|[marker_series::is_enabled-Methode](../profiling/marker-series-is-enabled-method.md)|Bestimmt, ob eine Sitzung den Anbieter aktiviert hat|  
|[marker_series::write_alert-Methode](../profiling/marker-series-write-alert-method.md)|Schreibt eine Warnung in die Ablaufverfolgungsdatei der Nebenläufigkeitsschnellansicht|  
|[marker_series::write_flag-Methode](../profiling/marker-series-write-flag-method.md)|Schreibt ein Flag in die Ablaufverfolgungsdatei der Nebenläufigkeitsschnellansicht|  
|[marker_series::write_message-Methode](../profiling/marker-series-write-message-method.md)|Schreibt eine Meldung in die Ablaufverfolgungsdatei der Nebenläufigkeitsschnellansicht|  
  
## <a name="inheritance-hierarchy"></a>Vererbungshierarchie  
 `marker_series`  
  
## <a name="requirements"></a>Anforderungen  
 **Header:** cvmarkersobj.h  
  
 **Namespace:** Concurrency::diagnostic  
  
## <a name="see-also"></a>Siehe auch  
 [diagnostic-Namespace](../profiling/diagnostic-namespace.md)