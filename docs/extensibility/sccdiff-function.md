---
title: "SccDiff-Funktion | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "SccDiff"
helpviewer_keywords: 
  - "SccDiff-Funktion"
ms.assetid: d49bc8c5-f631-4153-9d3c-feb3564da305
caps.latest.revision: 16
caps.handback.revision: 16
ms.author: "gregvanl"
manager: "ghogen"
---
# SccDiff-Funktion
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Diese Funktion zeigt \(oder optional für überprüft\) die Unterschiede zwischen der aktuellen Datei \(auf dem lokalen Datenträger\) und die zuletzt eingecheckte Version in der Quelle System steuern.  
  
## Syntax  
  
```cpp#  
SCCRTN SccDiff(  
   LPVOID    pvContext,  
   HWND      hWnd,  
   LPCSTR    lpFileName,  
   LONG      fOptions,  
   LPCMDOPTS pvOptions  
);  
```  
  
#### Parameter  
 pvContext  
 \[in\] Source Control\-Plug\-in Context\-Struktur.  
  
 hWnd  
 \[in\] Ein Handle für die IDE\-Fenster, das Quellcodeverwaltungs\-Plug\-in als übergeordnetes Element für alle Dialogfelder verwenden kann, die es bereitstellt.  
  
 lpFileName  
 \[in\] Name der Datei, für die die Differenz angefordert wird.  
  
 Bestanden  
 \[in\] Befehl Flags. Einzelheiten finden Sie unter "Hinweise".  
  
 pvOptions  
 \[in\] Quellcodeverwaltungs\-plug\-in spezifischen Optionen.  
  
## Rückgabewert  
 Datenquellen\-Steuerelement Plug\-in\-Implementierung dieser Funktion muss einen der folgenden Werte zurückgeben:  
  
|Wert|Beschreibung|  
|----------|------------------|  
|SCC\_OK|Die Arbeitsversion kopieren und Server sind identisch.|  
|SCC\_I\_FILESDIFFERS|Die Arbeitskopie unterscheidet sich von der Version unter quellcodeverwaltung.|  
|SCC\_I\_RELOADFILE|Eine Datei oder ein Projekt muss neu geladen werden.|  
|SCC\_E\_FILENOTCONTROLLED|Diese Datei befindet sich nicht in Datenquellen\-Steuerelement.|  
|SCC\_E\_NOTAUTHORIZED|Der Benutzer ist nicht zulässig, um diesen Vorgang auszuführen.|  
|SCC\_E\_ACCESSFAILURE|Es wurde ein Problem, das Zugriff auf Quellcode\-Verwaltungssystem, möglicherweise aufgrund eines Netzwerk\-oder Konflikte. Eine Wiederholung wird empfohlen.|  
|SCC\_E\_NONSPECIFICERROR|Unspezifischen Ausfall. Unterschiede wurde nicht abgerufen.|  
|SCC\_E\_FILENOTEXIST|Die lokale Datei wurde nicht gefunden.|  
  
## Hinweise  
 Diese Funktion dient zwei verschiedene Zwecke. Standardmäßig eine Liste der Änderungen in einer Datei angezeigt. Das Quellcodeverwaltungs\-Plug\-in wird in dem Format, das sie die Unterschiede zwischen der Datei auf dem Datenträger und die neueste Version der Datei unter quellcodeverwaltung anzeigen möchte, ein eigenen Fenster geöffnet.  
  
 Alternativ können Sie möglicherweise die IDE einfach zu bestimmen, ob eine Datei geändert wurde. Beispielsweise müssen die IDE zu bestimmen, ob eine Datei auschecken, ohne den Benutzer darüber informiert werden kann. In diesem Fall übergibt die IDE das `SCC_DIFF_CONTENTS` Flag. Das Quellcodeverwaltungs\-Plug\-in muss überprüfen Sie die Datei auf dem Datenträger byteweise gegen die quellcodeverwaltete Datei und einen Wert, der angibt, ob die beiden Dateien unterschiedlich sind, ganz ohne Anzeige für den Benutzer zurückgeben.  
  
 Das Quellcodeverwaltungs\-Plug\-In können als zur Optimierung der Leistung, Alternative basierend auf einer Prüfsumme oder einen Zeitstempel anstelle der Byte\-pro\-Byte\-Vergleich die von `SCC_DIFF_CONTENTS`: Diese Formen des Vergleichs werden offensichtlich schneller, aber weniger zuverlässig. Nicht alle Quellcode\-Verwaltungssysteme können diese alternative Vergleichsmethoden unterstützen, und das plug\-in möglicherweise auf einen Vergleich Inhalt zurück. Alle Source Control\-Plug\-ins müssen mindestens einen Vergleich Inhalt unterstützen.  
  
> [!NOTE]
>  Die schnelle Unterschied Flags schließen sich gegenseitig aus. Es ist keine Flags übergeben, aber kann nicht gleichzeitig mehrere übergeben.`SCC_DIFF_QUICK_DIFF`, ist eine Maske, die alle Flags kombiniert zum Testen verwendet werden können, aber sie sollten niemals als Parameter übergeben werden.  
  
|`fOption`|Bedeutung|  
|---------------|---------------|  
|SCC\_DIFF\_IGNORECASE|Zwischen Groß\-und Kleinschreibung \(kann für die schnelle oder visuelle Unterschiede verwendet werden\).|  
|SCC\_DIFF\_IGNORESPACE|Ignoriert Leerzeichen \(kann für die schnelle oder visuelle Unterschiede verwendet werden\).|  
|SCC\_DIFF\_QD\_CONTENTS|Im Hintergrund vergleicht die Datei byteweise.|  
|SCC\_DIFF\_QD\_CHECKSUM|Im Hintergrund vergleicht die Datei über eine Prüfsumme unterstützt. Wenn nicht unterstützt, wird ein Vergleich von Inhalt.|  
|SCC\_DIFF\_QD\_TIME|Im Hintergrund vergleicht die Datei über den Zeitstempel unterstützt. Wenn nicht unterstützt, wird ein Vergleich von Inhalt.|  
  
## Siehe auch  
 [Source Control\-Plug\-in\-API\-Funktionen](../extensibility/source-control-plug-in-api-functions.md)