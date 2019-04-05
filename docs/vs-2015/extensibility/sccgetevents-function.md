---
title: SccGetEvents-Funktion | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- SccGetEvents
helpviewer_keywords:
- SccGetEvents function
ms.assetid: 32f8147d-6dcc-465e-b07b-42da5824f9b0
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: d975570334aeab7c6709db92f3240a8e8d06b131
ms.sourcegitcommit: c496a77add807ba4a29ee6a424b44a5de89025ea
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/24/2019
ms.locfileid: "58956040"
---
# <a name="sccgetevents-function"></a>SccGetEvents-Funktion
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Diese Funktion ruft ein Statusereignis in der Warteschlange ab.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
SCCRTN SccGetEvents (  
   LPVOID pvContext,  
   LPSTR  lpFileName,  
   LPLONG lpStatus,  
   LPLONG pnEventsRemaining  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 pvContext  
 [in] Datenquellen-Steuerelement-Plug-in Context-Struktur.  
  
 lpFileName  
 [in, out] Der Puffer, in dem das Quellcodeverwaltungs-Plug-In für die zurückgegebenen Dateinamen (bis zu _MAX_PATH-Zeichen) versetzt.  
  
 lpStatus  
 [in, out] Gibt den Statuscode zurück (finden Sie unter [Datei Statuscode](../extensibility/file-status-code-enumerator.md) mögliche Werte).  
  
 pnEventsRemaining  
 [in, out] Anzahl der Einträge in der Warteschlange verbleibt, nach dem Aufruf zurückgegeben. Wenn diese Zahl groß ist, könnten sich der Aufrufer zum Aufrufen der [SccQueryInfo](../extensibility/sccqueryinfo-function.md) um alle Informationen auf einmal abzurufen.  
  
## <a name="return-value"></a>Rückgabewert  
 Die Source-Steuerelement-Plug-in-Implementierung dieser Funktion muss einen der folgenden Werte zurückgeben:  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|SCC_OK|Ruft Ereignisse erfolgreich war.|  
|SCC_E_OPNOTSUPPORTED|Diese Funktion wird nicht unterstützt.|  
|SCC_E_NONSPECIFICERROR|Nicht spezifischen Fehler.|  
  
## <a name="remarks"></a>Hinweise  
 Diese Funktion wird aufgerufen, während der Verarbeitung im Leerlauf befindet, um festzustellen, ob alle statusaktualisierungen für Dateien unter quellcodeverwaltung stattgefunden haben. Das Quellcodeverwaltungs-Plug-in verwaltet er den Status aller Dateien, die er kennt, und wenn eine Änderung des Status finden Sie durch das plug-in, den Status und die dazugehörige Datei in einer Warteschlange gespeichert werden. Wenn `SccGetEvents` aufgerufen wird, wird im oberen Bereich Element der Warteschlange abgerufen und zurückgegeben wird. Diese Funktion ist beschränkt, nur zuvor zwischengespeicherten Informationen zurückgegeben werden sollen, und benötigen einen sehr schnellen Turnaround (d. h. keine Lesen des Datenträgers oder Fragen das Quellcode-Verwaltungssystem für den Status) Andernfalls kann die Leistung der IDE gestartet, kann es zu Leistungseinbußen.  
  
 Ist kein Update Status Bericht, speichert das Quellcodeverwaltungs-Plug-in eine leere Zeichenfolge in den Puffer, der auf `lpFileName`. Andernfalls das plug-in speichert den vollständigen Pfadnamen der Datei für die die Statusinformationen geändert hat, und gibt den entsprechenden Statuscode zurück (einen der Werte finden Sie im [Datei Statuscode](../extensibility/file-status-code-enumerator.md)).  
  
## <a name="see-also"></a>Siehe auch  
 [Quellcodeverwaltungsfunktionen-Plug-in-API](../extensibility/source-control-plug-in-api-functions.md)   
 [Dateistatuscode](../extensibility/file-status-code-enumerator.md)
