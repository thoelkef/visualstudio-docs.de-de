---
title: SccDiff Funktion | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
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
ms.openlocfilehash: 30d8d6a4b8b400088d5feed663c8257215a0f8a1
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
ms.locfileid: "31138576"
---
# <a name="sccdiff-function"></a>SccDiff-Funktion
Diese Funktion zeigt (oder optional nur überprüft) die Unterschiede zwischen der aktuellen Datei (auf der lokalen Festplatte) und die zuletzt eingecheckte Version in der Quelle System steuern.  
  
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
  
#### <a name="parameters"></a>Parameter  
 pvContext  
 [in] Datenquellen-Steuerelement-Plug-in-Context-Struktur.  
  
 hWnd  
 [in] Ein Handle für die IDE-Fenster, das das Quellsteuerelement-Plug-in als übergeordnetes Element für alle Dialogfelder verwenden kann, die es bereitstellt.  
  
 lpFileName  
 [in] Der Dateiname für das die Differenz angefordert werden.  
  
 fOptions  
 [in] Befehl Flags. Einzelheiten finden Sie unter "Hinweise".  
  
 pvOptions  
 [in] Quellcodeverwaltungs-plug-in spezifischen Optionen.  
  
## <a name="return-value"></a>Rückgabewert  
 Die Source Control-Plug-in-Implementierung dieser Funktion muss einen der folgenden Werte zurückgeben:  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|SCC_OK|Die funktionierenden kopieren und Server-Version sind identisch.|  
|SCC_I_FILESDIFFERS|Die Arbeitskopie unterscheidet sich von der Version in der quellcodeverwaltung.|  
|SCC_I_RELOADFILE|Eine Datei oder ein Projekt muss erneut geladen werden.|  
|SCC_E_FILENOTCONTROLLED|Die Datei ist nicht in der quellcodeverwaltung.|  
|SCC_E_NOTAUTHORIZED|Der Benutzer ist nicht zulässig, um diesen Vorgang auszuführen.|  
|SCC_E_ACCESSFAILURE|Es wurde ein Problem, das Zugriff auf das Quellcodeverwaltungssystem, wahrscheinlich aufgrund eines Netzwerk-oder Konflikte. Eine Wiederholung wird empfohlen.|  
|SCC_E_NONSPECIFICERROR|Unspezifischen Fehlers; Unterschied der Datei wurde nicht abgerufen werden.|  
|SCC_E_FILENOTEXIST|Die lokale Datei wurde nicht gefunden.|  
  
## <a name="remarks"></a>Hinweise  
 Diese Funktion werden zwei verschiedenen Zwecken dient. Standardmäßig zeigt er eine Liste der Änderungen in einer Datei. Die Datenquellen-Steuerelement-Plug-in wird in dem Format, er die Unterschiede zwischen dem Benutzer die Datei auf dem Datenträger und die neueste Version der Datei unter quellcodeverwaltung anzeigen wählt, ein eigenen Fenster geöffnet.  
  
 Alternativ können Sie möglicherweise die IDE einfach zu bestimmen, ob eine Datei geändert wurde. Beispielsweise kann die IDE müssen zu bestimmen, ob eine Datei auschecken, ohne den Benutzer darüber informiert werden kann. In diesem Fall übergibt die IDE die `SCC_DIFF_CONTENTS` Flag. Die Datenquellen-Steuerelement-Plug-in muss überprüfen Sie die Datei auf dem Datenträger byteweise gegen die quellcodeverwaltete Datei und ein Rückgabewert gibt an, ob die beiden Dateien unterschiedlich sind, ohne dass eine Anzeige für den Benutzer.  
  
 Als zur Optimierung der Leistung, kann das Quellsteuerelement-Plug-in eine Alternative basierend auf einer Prüfsumme oder anstelle der Byte-pro-Byte-Vergleich für aufgerufen wird, indem Sie einen Zeitstempel verwenden `SCC_DIFF_CONTENTS`: Diese Formen des Vergleichs werden deutlich schneller, aber weniger zuverlässig. Nicht alle Quellcode-Verwaltungssysteme können diese Vergleichsmethoden alternative unterstützen, und das plug-in möglicherweise beim ausweichen auf einen Vergleich Inhalt. Alle Source Control-Plug-ins muss mindestens einen Vergleich Inhalt unterstützen.  
  
> [!NOTE]
>  Die schnelle Unterschied Flags schließen sich gegenseitig aus. Es ist zulässig, die keine Flags übergeben, aber es ist nicht zulässig, gleichzeitig mehrere übergeben. `SCC_DIFF_QUICK_DIFF`, also eine Maske, die alle Flags kombiniert zum Testen verwendet werden können, jedoch sollten Sie nie als Parameter übergeben werden.  
  
|`fOption`|Bedeutung|  
|---------------|-------------|  
|SCC_DIFF_IGNORECASE|Groß-und Kleinschreibung unterschieden (kann für die schnelle oder visuellen Unterschied verwendet werden).|  
|SCC_DIFF_IGNORESPACE|Ignoriert Leerraum (kann für die schnelle oder visuellen Unterschied verwendet werden).|  
|SCC_DIFF_QD_CONTENTS|Im Hintergrund vergleicht die Datei byteweise.|  
|SCC_DIFF_QD_CHECKSUM|Im Hintergrund vergleicht die Datei über eine Prüfsumme beim unterstützt. Wenn nicht unterstützt, ausgewichen, auf einem Vergleich des Inhalts.|  
|SCC_DIFF_QD_TIME|Im Hintergrund vergleicht die Datei über ihre Zeitstempel unterstützt. Wenn nicht unterstützt, ausgewichen, auf einem Vergleich des Inhalts.|  
  
## <a name="see-also"></a>Siehe auch  
 [API-Funktionen von Quellcodeverwaltungs-Plug-Ins](../extensibility/source-control-plug-in-api-functions.md)