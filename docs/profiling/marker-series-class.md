---
title: marker_series -Klasse | Microsoft-Dokumentation
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: cvmarkersobj/Concurrency::diagnostic::marker_series
helpviewer_keywords: Concurrency::diagnostic::marker_series class
ms.assetid: b8445ed0-c512-4f92-b6b4-3d05c044f939
caps.latest.revision: "3"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b326e88e18e3a7c5515cc11bfda7e5c35ae4a063
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="markerseries-class"></a>marker_series-Klasse
Stellt einen seriellen Kanal mit Ereignissen dar, die von einem einzelnen Anbieter generiert werden.  
  
## <a name="syntax"></a>Syntax  
  
```  
class marker_series;  
```  
  
## <a name="members"></a>Mitglieder  
  
### <a name="public-constructors"></a>Öffentliche Konstruktoren  
  
|Name|Beschreibung|  
|----------|-----------------|  
|[marker_series::marker_series-Konstruktor](../profiling/marker-series-marker-series-constructor.md)|Initialisiert eine neue Instanz der `marker_series`-Klasse.|  
|[marker_series::~marker_series-Destruktor](../profiling/marker-series-tilde-marker-series-destructor.md)|Zerstört das marker_series-Objekt und gibt alle zugewiesenen Ressourcen frei|  
  
### <a name="public-methods"></a>Öffentliche Methoden  
  
|Name|Beschreibung|  
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