---
title: SccGetEvents-Funktion | Microsoft-Dokumentation
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- SccGetEvents
helpviewer_keywords:
- SccGetEvents function
ms.assetid: 32f8147d-6dcc-465e-b07b-42da5824f9b0
caps.latest.revision: 14
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 1e73fea52d207d4f9834d5c3eabb15bf733c7e23
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47513168"
---
# <a name="sccgetevents-function"></a>SccGetEvents-Funktion
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [SccGetEvents-Funktion](https://docs.microsoft.com/visualstudio/extensibility/sccgetevents-function).  
  
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

