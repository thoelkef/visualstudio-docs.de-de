---
title: SccDiff-Funktion | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccDiff
helpviewer_keywords:
- SccDiff function
ms.assetid: d49bc8c5-f631-4153-9d3c-feb3564da305
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 68f90e406a06069403b76749977c5546b10ed790
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/02/2019
ms.locfileid: "53872053"
---
# <a name="sccdiff-function"></a>SccDiff-Funktion
Diese Funktion wird angezeigt (oder optional für überprüft) die Unterschiede zwischen der aktuellen Datei (auf dem lokalen Datenträger) und die zuletzt eingecheckte Version in der Quelle System steuern.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
SCCRTN SccDiff(  
   LPVOID    pvContext,  
   HWND      hWnd,  
   LPCSTR    lpFileName,  
   LONG      fOptions,  
   LPCMDOPTS pvOptions  
);  
```  
  
### <a name="parameters"></a>Parameter  
 pvContext  
 [in] Datenquellen-Steuerelement-Plug-in Context-Struktur.  
  
 hWnd  
 [in] Ein Handle für das IDE-Fenster, das das Quellcodeverwaltungs-Plug-in als übergeordnetes Element für alle Dialogfelder verwenden kann, die er bereitstellt.  
  
 lpFileName  
 [in] Der Dateiname für das die Differenz angefordert wird.  
  
 Bestanden  
 [in] Befehls-Flags. Einzelheiten finden Sie unter "Hinweise".  
  
 pvOptions  
 [in] Quellcodeverwaltungs-plug-in spezifischen Optionen.  
  
## <a name="return-value"></a>Rückgabewert  
 Die Source-Steuerelement-Plug-in-Implementierung dieser Funktion muss einen der folgenden Werte zurückgeben:  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|SCC_OK|Die funktionierende kopieren und Server-Version sind identisch.|  
|SCC_I_FILESDIFFERS|Die Arbeitskopie unterscheidet sich von der Version in der quellcodeverwaltung.|  
|SCC_I_RELOADFILE|Eine Datei oder ein Projekt muss neu geladen werden.|  
|SCC_E_FILENOTCONTROLLED|Die Datei ist nicht unter quellcodeverwaltung.|  
|SCC_E_NOTAUTHORIZED|Der Benutzer ist nicht zulässig, um diesen Vorgang auszuführen.|  
|SCC_E_ACCESSFAILURE|Es wurde ein Problem, das Zugriff auf das Quellcodeverwaltungssystem, möglicherweise aufgrund eines Netzwerk-oder-Konflikte bestehen. Eine Wiederholung wird empfohlen.|  
|SCC_E_NONSPECIFICERROR|Unspezifischen Fehlers; Unterschied der Datei wurde nicht abgerufen werden.|  
|SCC_E_FILENOTEXIST|Die lokale Datei wurde nicht gefunden.|  
  
## <a name="remarks"></a>Hinweise  
 Diese Funktion dient zwei verschiedene Zwecke. Standardmäßig zeigt er eine Liste der Änderungen in einer Datei an. Das Quellcodeverwaltungs-Plug-in wird ein eigenen Fenster, in dem Format, die die Unterschiede zwischen dem Benutzer die Datei auf dem Datenträger und die neueste Version der Datei unter quellcodeverwaltung Anzeige ausgewählt, geöffnet.  
  
 Alternativ müssen die IDE einfach zu bestimmen, ob eine Datei geändert hat. Beispielsweise müssen die IDE zu bestimmen, ob eine Datei auschecken, ohne den Benutzer darüber informiert werden kann. In diesem Fall übergibt die IDE die `SCC_DIFF_CONTENTS` Flag. Das Quellcodeverwaltungs-Plug-in muss überprüfen Sie die Datei auf dem Datenträger byteweise, für die Datei unter quellcodeverwaltung, und geben einen Wert, der angibt, ob die beiden Dateien unterschiedlich sind, ohne dass eine Anzeige für den Benutzer zurück.  
  
 Das Quellcodeverwaltungs-Plug-In können Leistung zu optimieren, basierte auf einer Prüfsumme oder einen Zeitstempel anstelle der Byte-pro-Byte-Vergleich für aufgerufen werden, indem Sie Alternative `SCC_DIFF_CONTENTS`: Diese Formen des Vergleichs werden offensichtlich schneller, aber weniger zuverlässig. Nicht alle Quellcode-Verwaltungssysteme können diese Vergleichsmethoden alternative unterstützen, und das plug-in möglicherweise beim ausweichen auf einen Vergleich der Inhalte. Alle Quellcodeverwaltungs-Plug-ins muss mindestens einen Vergleich Inhalt unterstützen.  
  
> [!NOTE]
>  Die Flags für die schnelle Unterschied schließen sich gegenseitig aus. Es ist zulässig, die keine Flags übergeben, aber es ist nicht zulässig, um mehrere Werte gleichzeitig zu übergeben. `SCC_DIFF_QUICK_DIFF`, d.h. eine Maske, die kombiniert alle Flags, die zum Testen verwendet werden können, aber sie sollten nie als Parameter übergeben werden.  
  
|`fOption`|Bedeutung|  
|---------------|-------------|  
|SCC_DIFF_IGNORECASE|Groß-/Kleinschreibung Vergleich (kann für schnelle oder visuellen Unterschied verwendet werden).|  
|SCC_DIFF_IGNORESPACE|Ignoriert Leerzeichen (kann für schnelle oder visuellen Unterschied verwendet werden).|  
|SCC_DIFF_QD_CONTENTS|Im Hintergrund werden Sie die Datei byteweise verglichen.|  
|SCC_DIFF_QD_CHECKSUM|Im Hintergrund vergleicht die Datei über eine Prüfsumme unterstützt. Wenn nicht unterstützt, fragt einen Vergleich der Inhalte.|  
|SCC_DIFF_QD_TIME|Im Hintergrund vergleicht die Datei über die Zeitstempel des Zeitpunkts, unterstützt. Wenn nicht unterstützt, fragt einen Vergleich der Inhalte.|  
  
## <a name="see-also"></a>Siehe auch  
 [Datenquellen-Steuerelement-Plug-in-API-Funktionen](../extensibility/source-control-plug-in-api-functions.md)