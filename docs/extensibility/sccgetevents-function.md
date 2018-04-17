---
title: SccGetEvents Funktion | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- SccGetEvents
helpviewer_keywords:
- SccGetEvents function
ms.assetid: 32f8147d-6dcc-465e-b07b-42da5824f9b0
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 79e517d87acd61eafcd2eb0a12f5a8978912db81
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="sccgetevents-function"></a>SccGetEvents-Funktion
Diese Funktion ruft ein Statusereignis in der Warteschlange ab.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
SCCRTN SccGetEvents (  
   LPVOID pvContext,  
   LPSTR  lpFileName,  
   LPLONG lpStatus,  
   LPLONG pnEventsRemaining  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 pvContext  
 [in] Datenquellen-Steuerelement-Plug-in-Context-Struktur.  
  
 lpFileName  
 [in, out] Puffer, in dem die Quelle zu steuern-Plug-in, setzt die zurückgegebenen Dateinamen (bis zu _MAX_PATH-Zeichen).  
  
 lpStatus  
 [in, out] Gibt den Statuscode zurück (finden Sie unter [Statuscode "Datei"](../extensibility/file-status-code-enumerator.md) mögliche Werte).  
  
 pnEventsRemaining  
 [in, out] Gibt die Anzahl von Einträgen, die nach diesem Aufruf in der Warteschlange verbleibt. Wenn diese Zahl groß ist, kann der Aufrufer entscheiden, zum Aufrufen der [SccQueryInfo](../extensibility/sccqueryinfo-function.md) um alle Informationen auf einmal abzurufen.  
  
## <a name="return-value"></a>Rückgabewert  
 Die Source Control-Plug-in-Implementierung dieser Funktion muss einen der folgenden Werte zurückgeben:  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|SCC_OK|Ruft Ereignisse erfolgreich war.|  
|SCC_E_OPNOTSUPPORTED|Diese Funktion wird nicht unterstützt.|  
|SCC_E_NONSPECIFICERROR|Unspezifischen Fehlers.|  
  
## <a name="remarks"></a>Hinweise  
 Diese Funktion wird aufgerufen, während der Verarbeitung im Leerlauf, um festzustellen, ob alle Updates des Abonnementstatus für Dateien unter quellcodeverwaltung stattgefunden haben. Die Datenquellen-Steuerelement-Plug-in verwaltet er den Status aller Dateien, die bekannten, und wenn eine Änderung des Status ist vermerkt Plug-Ins, den Status und die zugehörige Datei in einer Warteschlange gespeichert werden. Wenn `SccGetEvents` aufgerufen wird, werden die obersten Element der Warteschlange abgerufen und zurückgegeben wird. Diese Funktion ist beschränkt, nur zuvor zwischengespeicherten Informationen zurückgegeben werden sollen, und benötigen einen sehr realisieren (d. h. keine des Datenträgers beim Lesen oder Status im Quellcodeverwaltungssystem zur); Andernfalls kann die Leistung der IDE starten, zu verringern.  
  
 Ist keine Aktualisierung des Clientstatus Bericht, speichert das Quellsteuerelement-Plug-in eine leere Zeichenfolge in den Puffer verweist `lpFileName`. Andernfalls das plug-in speichert den vollständigen Pfadnamen der Datei für die die Statusinformationen geändert hat, und gibt den entsprechenden Statuscode zurück (einen der Werte detaillierte [Statuscode "Datei"](../extensibility/file-status-code-enumerator.md)).  
  
## <a name="see-also"></a>Siehe auch  
 [Quellcodeverwaltungsfunktionen-Plug-in-API](../extensibility/source-control-plug-in-api-functions.md)   
 [Statuscode "Datei"](../extensibility/file-status-code-enumerator.md)